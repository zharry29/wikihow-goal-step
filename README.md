# Goal-Step Reasoning with WikiHow
This repository contains data and code accompanying the paper "Reasoning about Goals, Steps, and Temporal Ordering with WikiHow" by Lyu Qing, Li Zhang and Chris Callison-Burch. If you use our resources, please cite the following paper:
```
@misc{lyu2020reasoning,
    title={Reasoning about Goals, Steps, and Temporal Ordering with WikiHow},
    author={Qing Lyu and Li Zhang and Chris Callison-Burch},
    year={2020},
    eprint={2009.07690},
    archivePrefix={arXiv},
    primaryClass={cs.CL}
}
```

## WikiHow Corpus
We crawled the [wikiHow](https://www.wikihow.com/Main-Page) website as of July 2020, and release the resulting **wikiHow Corpus** [here](https://drive.google.com/drive/folders/1JF_1lbfCflXW7WLzzkLWinfiaHd8Rhdr?usp=sharing). Each article is represented by a json file, including information such as title,  url, description, category, methods or parts, step headline, step description, author information, time last updated, rating, videos, related articles, tips and warnings, Q&A, references, quizzes, links to other languages, related articles, etc. 

## WikiHow Goal-Step Inference Task
We derive 3 multiple choice tasks from wikiHow. The training data and benchmark data can be found [here](https://drive.google.com/drive/folders/1apXhFeo3fKRppuiwj2WoOuNp73H5cLF6?usp=sharing). In each article, we define **Goal** as the title without "How to" (e.g. Do Yoga), and **Step** as the header of each paragraph (e.g. Warm up). 
1. *Step Inference*. Given a prompt goal and 4 candidate steps, choose the step that helps achieve the goal.
2. *Goal Inference*. Given a prompt step and 4 candidate goals, choose the correct goal which the step helps achieve.
3. *Step Ordering*. Given a prompt goal and 2 steps, determine which step temporally precedes the other.

## Pretrained Models
All our models are implemented using [HuggingFace Transformers](https://github.com/huggingface/transformers) and are hosted on its model hub. You can find the models [here](https://huggingface.co/zharry29). To use our pretrained models, simply install the library (and its dependencies) and import our models. A model is named as `zharry29/[task]_benchmark_[modelName]`:
- [task] is `step` for Step Inference, `goal` for Goal Inference, and `order` for Step Ordering. 
- [modelName] is `roberta` for RoBERTa, `bert` for BERT, `xlnet` for XLNet, and `gpt` for GPT-2. 
For example, `zharry29/goal_benchmark_roberta` is the name for the RoBERTa model pretrained on the training data of the Goal Inference task.
