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
  * full fine-tuning > The process results in a new version of the model with updated weights.
  * Evaluate performance
* Fine-tuning on a single task
  * drawbacks: catastrophic forgetting=forget other tasks(changed W and bad result on other tasks)
  * Solution: If you need a single task, the drawback is not a big deal. if not:
    * Multitask tine tuning
    * Perform parameter-efficient fine-tuning or PEFT
* Multitask tine tuning
  * FLAN: is a specific set of instructions used to fine-tune different models. FLAN-T5, the FLAN instruct version of the T5 foundation model
* Model Evaluate
  * cross entropy function
  * 
* Parameter efficient fine-tuning (PEFT)
* 
