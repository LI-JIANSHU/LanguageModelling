## Overview
 * SPNLM training:
  - The first trial: sentences begins with `<s>` and ends with `</s>`
  - The second trial: sentences begins as usual and ends with `</s>`
  - Adding grams from evaluation dataset, the first trial 
  - Adding grams from evaluation dataset, the second trial

---

## Summary of Resuls
 * Kaldi-Swbd-s5b: run.sh, with fisher. This is the baseline of comparison. The result is <a href='Results/kaldi_result'>here</a>.  
 * Perplexity analysis
 - Perplexity analysis for various LM. The result is <a href='Results/ppl_analysis'>here</a>
 - The second Perplexity analysis for various LM. The result is <a href='Results/ppl_analysis2'>here</a>
 * Running with the first trial of adding grams from evaluation dataset
 - Worse than the baseline.
 
 * Running with the second trial of adding grams from evaluation dataset
 - Grams from evaluation dataset only, with recalculation of backoff weight.The result is <a href='Results/eval_v2_rebow'>here</a>
 - Grams from both training set and evaluation set, with recalculation of backoff weight. The result is <a href='Results/sw1_addeval2_rebow'>here</a> 
 - Grams from evaluation dataset only. The result is <a href='Results/eval_v2'>here</a>
 - Grams from both training set and evaluation set. The result is <a href='Results/sw1_addeval2'>here</a>
---

 
 
