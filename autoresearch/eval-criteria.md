# Eval Criteria: Launch Announcement Writer

The scoring function the optimization loop ran each round. 25 sample inputs (real feature specs), each output scored on 4 binary checks. Score = average across all inputs and checks.

### 1. Contains at least one concrete number
PASS: "cuts scheduling time from 4 clicks to 1."
FAIL: "makes scheduling much faster."

### 2. No banned buzzwords
Banned: revolutionary, seamless, game-changing, cutting-edge, robust, leverage, synergy, delight, unlock, supercharge.
PASS: "You can now reschedule in one tap."
FAIL: "A revolutionary, seamless way to unlock scheduling."

### 3. States who it's for and what they can now do
PASS: "Admins can now bulk-edit permissions for up to 500 users at once."
FAIL: "We shipped a new permissions feature."

### 4. Length 40-120 words
PASS: a focused paragraph.
FAIL: a one-liner, or a three-paragraph essay.
