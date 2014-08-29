## Introduction to language model format:  ARPA
 * It is a commonly used file format for LM, a lot of toolkits are available to generate the LM format: <a href='http://www.speech.cs.cmu.edu/SLM/toolkit.html'> CMU-LM</a>, <a href='http://projects.csail.mit.edu/cgi-bin/wiki/view/SLS/MITLMTutorial'> MIT-LM</a>, <a href='http://www.speech.sri.com/projects/srilm/'> SRILM</a>, <a href='https://hlt.fbk.eu/technologies/irstlm-irst-language-modelling-toolkit'> IRSTLM </a>, ect. The input to the toolkits are usually a training text file with transcriptions, one sentence per line. The beginning of sentence tag "\<s>" and end of sentence tag "\</s>" are usually inserted automatically. The various kinds of smoothing methods can be applied at your own choice. 
 * There are a lot of toolkits available to generate ARPA format LM. The content of ARPA LM is also quite clear if you looked into one of the ARPA files. One sample ARPA file looks like:

```
\data\
ngram 1=30248
ngram 2=455653
ngram 3=272635

\1-grams:
-5.644002	!sil
-5.106135	-'s	-0.1416712
-5.644002	-'t
-5.490593	-1k	-0.1416712
-5.490593	-able	-0.1416712
-5.644002	-ains
-4.99885	-an	-0.1416712

\2-grams:
-2.990698	plan whatsoever
-1.682168	plan where	-0.115172
-2.186728	plan which
-2.618273	plan with
-2.968209	plan worked

\3-grams:
-0.2829364	the zipper went
-0.2700108	time zone </s>
-0.6325949	twilight zone rules
-0.2700108	war zone </s>
-0.2056841	the zoo and

\end\
```

The meta data begins with tag \data\, then the total numbers of each n-gram are listed. Under each \N-gram tag, the N-grams are listed as:
`probability n-gram (backoff probability)`
The probabilities are often in log10 domain and the backoffs are optional. It will also contain some headings giving additional information.
 
 ---
 
## How the ARPA file is generated. 
Although there are a lot of toolkits to generate LM in ARPA format, there is not much documentation about how it is generated. Here is what I found about it.
 * How the number of N-grams are decided
   - **Unigram**: It is the easiest one to generate from the training dataset. Just list every single words (including `<s>` and `</s>` ) in the training set and remove the repeated words. In other words, the number of unigrams is the number of unique words in the training set. 
   
   - **Bigram**: For a sentence with N words, including `<s>` and `</s>`, N+1 bigrams can be built as:
``   `<s>` w1;  w1 w2; w2 w3; ... wN `</s>`; ``. 
List all the bigrams from all the sentences and then remove the duplicated bigrams. Then you can get the list of bigrams in the ARPA file.
   - **Trigram**: For a sentence with N words, including `<s>` and `</s>`, N trigrams can be built. List all the trigrams from all the sentences and then remove the duplicated trigrams. As each trigram is less likely to repeat itself, the number of unique trigrams is much larger than that of bigrams. One more step is carried out, i.e., the trigrams that appears only once is the training dateset is removed. After this step, the remaining trigrams are the ones you find in the ARPA file. 
   - Higher N-gram: The same procudure in **Trigram** is applied.

 * The remaining steps to build a ARPA format LM
Various smoothing, discounting methods can be applied to calculate the probabilities of the N-grams and the backoff probabilities. It is not discussed here, as the documentation in the LM toolkits will always cover them. 
