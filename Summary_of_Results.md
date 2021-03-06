## Overview
 * SPNLM training:
  - The first trial: sentences begins with `<s>` and ends with `</s>`
  - The second trial: sentences begins as usual and ends with `</s>`
 * Handling the grams
  - Adding grams from evaluation dataset, the first trial 
  - Adding grams from evaluation dataset, the second trial

---

## Summary of Resuls
 * Kaldi-Swbd-s5b: run.sh, with fisher. This is the baseline of comparison. The result is <a href='Results/kaldi_result'>here</a>.  
 * Perplexity analysis
  - Perplexity analysis for various LM. The result is <a href='Results/ppl_analysis'>here</a>
  - The second Perplexity analysis for various LM. The result is <a href='Results/ppl_analysis2'>here</a>
  - The third Perplexity analysis for various LM. Result is <a href='Results/ppl_analysis3'>here</a>
 * Running with the first trial of adding grams from evaluation dataset
  - Worse than the baseline.
 
 * Running with the second trial of adding grams from evaluation dataset. (Format: baseline, baseline with fisher, new LM, new LM with fisher)
  - Grams from evaluation dataset only. The result is <a href='Results/eval_v2'>here</a>
  - Grams from evaluation dataset only, with recalculation of backoff weight. The result is <a href='Results/eval_v2_rebow'>here</a>
  - Grams from both training set and evaluation set. The result is <a href='Results/sw1_addeval2'>here</a>
  - Grams from both training set and evaluation set, with recalculation of backoff weight. The result is <a href='Results/sw1_addeval2_rebow'>here</a>
  
* In the second trial of adding grams from evaluation dataset, the unigrams are unchanged and are directly from evaluation dataset. It is a piece of additional information and should not appear in the new LM. In the third trial, the unigrams are modified according to the original LM from training dataset. 
* Running with the third trial of adding grams from evaluation dataset. (Format: baseline, baseline with fisher, new LM, new LM with fisher, new LM with fisher with equal weights)
   - Grams from evaluation dataset only, with a dummy backoff weight of -10. A BOW -10 is effectively -Inf and this manipulation will force the program to use higher order grams instead of lower ones. The result is <a href='Results/eval_spn_dumbow'>here</a>
   - Grams from both training set and evaluation set, with a dummy backoff weight of -10. The result is <a href='Results/sw1_addeval3_dumbow'>here</a>
  
  
 
---

 
 
