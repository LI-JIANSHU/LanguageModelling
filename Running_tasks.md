## Overview
 * SPNLM training:
  - The first trial: sentences begins with `<s>` and ends with `</s>`
  - The second trial: sentences begins as usual and ends with `</s>`

---

## Local laptop:
 * Kaldi-Swbd-s5b: run.sh, with fisher (killed) 
 * Calculating probabilities for training Trial 2. 

---

## AI1:
 * Kaldi-Swbd-s5b: run.sh, with fisher
    
---

## ML1:
 * Kaldi-SWBD-s5b: run.sh, without fisher, using arpa from the first trail of SPNLM training
 * SPNLM training, the second trial, both 1-spn and 2-spn (finished)
 * Evaluate the probabilities and create new arpa files using weights from SPNLM training Trial 2
 
---
