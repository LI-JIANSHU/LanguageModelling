## Overview
 * SPNLM training:
  - The first trial: sentences begins with `<s>` and ends with `</s>`
  - The second trial: sentences begins as usual and ends with `</s>`

---

## Local laptop:
 * Kaldi-Swbd-s5b: run.sh, with fisher (killed) 
 * Calculating probabilities for training Trial 2 (uncomplete). 
 * Perplexity analysis for various LM. Result is <a href='Results/ppl_analysis'>here</a>

---

## AI1:
 * Kaldi-Swbd-s5b: run.sh, with fisher. (finished) 
The result <a href='Results/swbd_run'>here</a> is similar to that given in Kaldi. The result is formatted <a href='Results/kaldi_result'>here</a>. 
 * run_spnlm.sh. Using the new ARPA files on top of the finished run.sh. The most updated result is <a href='Results/most_updated'>here</a>.  (killed)
 * run_spnlm.sh new_arpas/eval2000.spnlm.rebow.arpa.gz (aborted, the G.fst can't be composed with L.fst, as G.fst is too small and they do not match)
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval.arpa.gz. (partial finished). Result is <a href='Results/spnlm_addeval'>here</a>
    
---

## ML1:
 * Kaldi-SWBD-s5b: run.sh, without fisher, using arpa from the first trial of SPNLM training. (finished) There are two independent running, results are here: <a href='Results/training_trial1_r1'>result1</a> and  <a href='Results/training_trial1_r2'>result2</a>.
 * SPNLM training, the second trial, both 1-spn and 2-spn (finished)
 * Evaluate the probabilities and create new arpa files using weights from SPNLM training Trial 2. (finished)
 * Kaldi-SWBD-s5b: run_with_spnlm.sh, with fisher option, using arpa from the second trial of SPNLM training. (finished with problem, Manually run the decoding stage) The result is <a href='Results/spnlm_trial2'>here</a>. 
 * spnlm_step/pure_decoding.sh. (killed, good except for tri4a_fmmi and tri4b_fmmi)
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval_rebow.arpa.gz (partial finished). Result is <a href='Results/spnlm_addeval_rebow'>here</a>
 
---
