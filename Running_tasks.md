## Overview
 * SPNLM training:
  - The first trial: sentences begins with `<s>` and ends with `</s>`
  - The second trial: sentences begins as usual and ends with `</s>`
 * Handling the grams
  - Adding grams from evaluation dataset, the first trial
  - Adding grams from evaluation dataset, the second trial

---

## Local laptop:
 * Kaldi-Swbd-s5b: run.sh, with fisher (killed) 
 * Calculating probabilities for training Trial 2 (uncomplete). 
 * Perplexity analysis for various LM. Result is <a href='Results/ppl_analysis'>here</a>
 * The second Perplexity analysis for various LM. Result is <a href='Results/ppl_analysis2'>here</a>
 * Training 1,2-SPN
 * Training 2SPN from weights in 1SPN (always get nan, stopped)
 * The third Perplexity analysis for various LM. Result is <a href='Results/ppl_analysis3'>here</a>

---

## AI1:
 * Kaldi-Swbd-s5b: run.sh, with fisher. (finished) 
The result <a href='Results/swbd_run'>here</a> is similar to that given in Kaldi. The result is formatted <a href='Results/kaldi_result'>here</a>. 
 * run_spnlm.sh. Using the new ARPA files on top of the finished run.sh. The most updated result is <a href='Results/most_updated'>here</a>.  (killed)
 * run_spnlm.sh new_arpas/eval2000.spnlm.rebow.arpa.gz (aborted, the G.fst can't be composed with L.fst, as G.fst is too small and they do not match)
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval.arpa.gz. (Finished). Result is <a href='Results/spnlm_addeval'>here</a>
 * run_spnlm.sh eval2000_v2_spnlm_rebow.arpa.gz (Finished). Result is <a href='Results/eval_v2_rebow'>here</a>
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval2_rebow.arpa.gz. (Finished) Result is <a href='Results/sw1_addeval2_rebow'>here</a>
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval3_dumbow.arpa.gz. (Finished) Result is <a href='Results/sw1_addeval3_dumbow'>here</a>
 * run_spnlm.sh fisher, modified unigrams with fixed "\<unk\>" probability, dummy the BOW at the very last stage. The resutl is [here](Results/mu2_dum)
 * run_spnlm.sh  mixure of sw1,fisher,eval_spn with equal weights and the pruned version of it. The result is [here](Results/fish_mix_all)
 * Decode deeplearn AM for various LMs. Result is [here](Results/deeplearn2)
 * Decode deeplearn AM (modified, add two more fully connected layers). Result is [here](Results/deeplearn_swbd)
 * Decode deeplearn AM, longer training time. Result is [here](Results/deeplearn_swbd_long_train)
 * Change the training parameters: parameters initialized from CNN, momentum is fixed, learning rate is small (the one after CNN fine-tune stage), no l2_decay is applied. The result is [here](Results/deeplearn_swbd_ini_cnn). The validate error rate in the training log is [here](Results/deeplearn_swbd_training_log)
    
---

## ML1:
 * Kaldi-SWBD-s5b: run.sh, without fisher, using arpa from the first trial of SPNLM training. (finished) There are two independent running, results are here: <a href='Results/training_trial1_r1'>result1</a> and  <a href='Results/training_trial1_r2'>result2</a>.
 * SPNLM training, the second trial, both 1-spn and 2-spn (finished)
 * Evaluate the probabilities and create new arpa files using weights from SPNLM training Trial 2. (finished)
 * Kaldi-SWBD-s5b: run_with_spnlm.sh, with fisher option, using arpa from the second trial of SPNLM training. (finished with problem, Manually run the decoding stage) The result is <a href='Results/spnlm_trial2'>here</a>. 
 * spnlm_step/pure_decoding.sh. (killed, good except for tri4a_fmmi and tri4b_fmmi)
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval_rebow.arpa.gz (Finished). Result is <a href='Results/spnlm_addeval_rebow'>here</a>
 * run_spnlm.sh eval2000_v2_spnlm.arpa.gz (Finished). Result is <a href='Results/eval_v2'>here</a>
 * run_spnlm.sh sw1.o3g.kn_spnlm_addeval2.arpa.gz. (Finished) Result is <a href='Results/sw1_addeval2'>here</a>
 * run_spnlm.sh eval_spn_dumbow.arpa.gz (Finished). Result is <a href='Results/eval_spn_dumbow'>here</a>
 * run_spnlm.sh fisher trimmed sw1.o3g.kn (trimmed according to the grams in the evaluation dataset). Result is [here] (Results/fish_and_trimmed_sw1)
 * Decode deeplearn AM for various LMs. Result is [here](Results/deeplearn1)
 
---
