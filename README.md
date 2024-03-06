# SamplingLLM

LLMs are trained to predict the next token, and yet are used to generate long text. While this undoubtedly works very well, I think the mismatch between those two task leads to substantial problems.

One of these problems for instance is that of repeating or degrading behavior of LLMs. Remedies are random sampling (i.e. top-p) or repetition penalties, yet they don't seem to address the root of the problem. (Newer and larger models seem to be better at it, why?)

# Hpyothesis
My Hypothesis is that part of the root cause might be successive duplicate tokens in the trainset. If a model is trained with the text "t1 t2 t2 t3" then for the second timestep the model only has to infer t2->t2. This is of course trivial to do and might lead the model to degrading behavior.

Now this raises the question if LLMs in principle are able to learn from data that contains successive duplicates. It might be that there is nothing to gain from t->t examples and they should be removed even if the text we want to model might be something like "I I I... think that..."
