# Larg Language Model  
## List of contents  
Week 1  
* Transformer Network
* Genitive AI Project Life Cycle
* Prompt Engineering
  
Week 2
* Instruction fine-tunning
  * Increase performance of the existing model for specific use case > using fine-tuning > to further train a base model
  * fine-tuning with instruction prompt > fine-tune LLM = instruct LLM
  * use an existing dataset with [prompt, completion] > supervised learning instead of self supervised learning
  * full fine-tuning: every model weight is updated. The process results in a new version of the model with updated weights.
  * Evaluate performance
* Fine-tuning on a single task
  * drawbacks: catastrophic forgetting=forget other tasks(changed W and bad result on other tasks)
  * Solution: If you need a single task, the drawback is not a big deal. if not:
    * Multitask fine tuning
    * Perform parameter-efficient fine-tuning(PEFT)
* Multitask fine tuning
  * FLAN: is a specific set of instructions used to fine-tune different models. FLAN-T5, the FLAN instruct version of the T5 foundation model
* Model Evaluate
  * Rouge > text summarization
  * Bleu score > text translation
* Benchmark
  * Using pre-existing datasets and associated benchmarks
  * Benchmark: GLUE, SuperGLUE and HELM
  * 
* Parameter efficient fine-tuning (PEFT): update a small set of subparameters > less prone to catastrophic forgetting: because original LLM slightly modified
  * update a small number of weights + small footprint overall + small adaptation to each task
  * Three main classes of PEFT method:
    * Selective: fine-tune only a subset of parameters. They could be specific layers of a certain component.
    * Reparametrization: it reduces the number of parameters to train by creating new low-rank transformations of the original network weights(LoRA).
    * Additive: It keeps all of the original LLM weights frozen and introduces new trainable components. there are two approches:
      *  Adapter methods add new trainable layers to the architecture of the model, typically inside the encoder or decoder components after the attention or feed-forward layers.
      *  Soft prompt methods keep the model architecture fixed and frozen, and focus on manipulating the input to achieve better performance. This can be done by adding trainable parameters to the prompt embeddings or keeping the input fixed and retraining the embedding weights. 
* Low-rank Adaptation(LoRA) is a parameter-efficient fine-tuning technique  
  * After the embedding vectors are created, they're fed into the self-attention layers where a series of weights are applied to calculate the attention scores. During full fine-tuning, every parameter in these layers is updated.
  *  LoRA is a strategy that reduces the number of parameters to be trained during fine-tuning by freezing all of the original model parameters and then injecting a pair of rank decomposition matrices alongside the original weights.
  *   The dimensions of the smaller matrices are set so that their product is a matrix with the same dimensions as the weights they're modifying. And then, we train the smaller matrices.
  *   [original weights] + B*A
  *   Applying LoRA to the self-attention layers of the model is often enough to fine-tune for a task and achieve performance gains. However, you can also use LoRA on other components like the feed-forward layers.
*   Soft prompt ( prompt tuning not prompt engineering)
  *  Prompt tuning: you add additional trainable tokens to your prompt and leave it up to the supervised learning process to determine their optimal values.
  *  Softprompt: The set of trainable tokens is called a soft prompt. It gets prepended to embedding vectors that represent your input text.
  *  The tokens that represent natural language are hard (fixed location in the embedding vector space). However, the soft prompts are not fixed discrete words of natural language.
