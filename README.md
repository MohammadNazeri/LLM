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
