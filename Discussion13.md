# 1

1. IF temperature > 100.4°F THEN the patient has a fever.
2. IF a patient has chest pain AND shortness of breath THEN seek emergency medical evaluation.
3. IF a patient is allergic to penicillin THEN do not prescribe penicillin-based antibiotics.

# 2
## What does the ML model predict?

The ML model predicts NOT FRAUD, because the fraud probability is 0.42, which is below the fraud threshold.

## What does the symbolic rule decide?

The symbolic rule says:

IF amount > $10,000 THEN flag as FRAUD.

Since the transaction amount is $12,500, the symbolic rule decides FRAUD.

## Which decision should override in a high-risk setting, and why?

In a high-risk setting like finance, the symbolic rule should override the ML prediction. This is because financial systems often need strict safety and compliance rules. Even though the ML model predicts not fraud, the transaction amount is above $10,000, which may require extra review. The symbolic rule acts as a hard constraint to reduce risk and ensure suspicious or high-value transactions are flagged. So the final decision should be to flag as FRAUD or send for manual review.

# 3
## Step 1: Apply R1

WM = {fever, cough}

Apply R1: If fever AND cough → flu

WM = {fever, cough, flu}

## Step 2: Apply R2

WM = {fever, cough, flu}

Apply R2: If flu → recommend antiviral

Add recommend antiviral to working memory.

WM = {fever, cough, flu, recommend antiviral}

## Step 3: Check R3

WM = {fever, cough, flu, recommend antiviral}

R3 says: If antiviral prescribed → schedule follow-up

However, the working memory contains recommend antiviral, not antiviral prescribed.  These are not exactly the same fact. Therefore, R3 cannot be applied unless we treat “recommend antiviral” as equivalent to “antiviral prescribed.”

### Final Working Memory

Using the rules exactly as written:

WM = {fever, cough, flu, recommend antiviral}

If “recommend antiviral” is treated as “antiviral prescribed,” then R3 would also apply, giving:

WM = {fever, cough, flu, recommend antiviral, schedule follow-up}

But strictly, the final answer is:

WM = {fever, cough, flu, recommend antiviral}

# 4. Mini Hybrid AI Concept
## What does the neural model predict?

Since temp = 102, and 102 > 100, the neural model predicts flu.

## What does the symbolic rule require?

The symbolic rule says that IF cough = False THEN illness != flu. Since cough = False, the symbolic rule requires that illness is not flu.

### How should a hybrid system resolve the conflict? Why?

The hybrid system should let the symbolic rule override the neural model. The neural model predicts flu, but the symbolic rule says that if there is no cough, the illness cannot be flu. To maintain logical consistency, the system should respect the symbolic rule as a hard constraint.

A good hybrid decision would be to either determine not flu, possibly cold, or needs further evaluation. The reason is that symbolic rules can represent strict medical constraints or expert knowledge. If the neural model output violates a rule constraint, the hybrid system should revise or reject the neural prediction.
