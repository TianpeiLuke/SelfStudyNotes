---
tags: 
aliases: 
date of note: 2025-07-01
---
## The Two Phases of Pipeline Creation

This is a critical point about SageMaker Pipelines that isn't always obvious: pipeline creation happens in two distinct phases:

1. __Definition Phase__: Where we're creating the pipeline structure, DAG, and defining connections.

   - This is when our logs are showing the error
   - The actual output values don't exist yet because no step has run

2. __Execution Phase__: When the pipeline actually runs in SageMaker.

   - This happens later, after definition
   - Steps execute and outputs become available

## Why This Is Normal

The error you're seeing is happening during the __Definition Phase__. At this point:

1. The `model_packaging` step hasn't executed yet, so it has no outputs
2. The `payload_test` step hasn't executed yet, so it has no outputs
3. The `model_registration` step is trying to validate that it has all required inputs

But the validation should be happening at execution time, not definition time!

## The Real Fix

Our DAG changes are correct - we fixed the *naming* issue. But we need to improve the `ModelRegistrationStepBuilder` to be more tolerant during the __Definition Phase__.

The builder should:

1. Recognize when it's in the Definition Phase
2. Skip certain validations that can only be done at Execution Phase
3. Trust that the DAG connections (which we fixed) will provide the right data at runtime

This is why our first attempt with all the property path registrations was critical - it was trying to help the builder locate properties at definition time.










-----------
##  Recommended Notes