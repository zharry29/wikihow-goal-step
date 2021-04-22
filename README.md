# Goal-Step Reasoning with WikiHow
This repository contains pointers to data and models accompanying the paper "Reasoning about Goals, Steps, and Temporal Ordering with WikiHow" by Lyu Qing, Li Zhang and Chris Callison-Burch. 

## WikiHow Corpus
We crawled the [wikiHow](https://www.wikihow.com/Main-Page) website as of July 2020, and release the resulting **wikiHow Corpus** [here](https://drive.google.com/file/d/1oL3b3VZuroEe19QPMgV9dEvcKhNvaSWm/view?usp=sharing). Each article is represented by a json file, including information such as title,  url, description, category, methods or parts, step headline, step description, author information, time last updated, rating, videos, related articles, tips and warnings, Q&A, references, quizzes, links to other languages, related articles, etc. The complete, unprocessed crawl image is [here](https://drive.google.com/file/d/1l19zf-G84qIOisxDWcCHlBLwKcXyERs6/view?usp=sharing), which is achieved by the following code:

> wget --wait=5 --random-wait --limit-rate=512k --timeout=3 -e robots=off --mirror -U 'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36' https://www.wikihow.com/



## WikiHow Goal-Step Inference Task
We derive 3 multiple choice tasks from wikiHow. The training data and benchmark data can be found [here](https://drive.google.com/drive/folders/1_c_sWbLbMe4_VcEAiNC8DSyBDi21jx9G?usp=sharing). In each article, we define **Goal** as the title without "How to" (e.g. Do Yoga), and **Step** as the header of each paragraph (e.g. Warm up). 
1. *Step Inference*. Given a prompt goal and 4 candidate steps, choose the step that helps achieve the goal.
2. *Goal Inference*. Given a prompt step and 4 candidate goals, choose the correct goal which the step helps achieve.
3. *Step Ordering*. Given a prompt goal and 2 steps, determine which step temporally precedes the other.
The negative candidates are sampled using an approach based on semantic similarity, and the code to do so is NOT included here. Please read our paper for more details, and contact us for special need of said code. 

## Pretrained Models
[This notebook](https://colab.research.google.com/drive/16Qz4fp6eFHd0OGTITTHvw7sZo1Qe_VOS?usp=sharing) demonstrates how to load and use our pretrained models. It is recommended that you run the notebook using Google Colab to avoid dependency issues.

All our models are implemented using [HuggingFace Transformers](https://github.com/huggingface/transformers) and are hosted on its model hub. You can find the models [here](https://huggingface.co/zharry29). To find hyperparameters, open the link, click on the model name, click on "List all files in model", and then load `training_args.bin` using PyTorch. To use our pretrained models, simply install the library (and its dependencies) and import our models. A model is named as `zharry29/[task]_benchmark_[modelName]`:
- [task] is `step` for Step Inference, `goal` for Goal Inference, and `order` for Step Ordering. 
- [modelName] is `roberta` for RoBERTa, `bert` for BERT, `xlnet` for XLNet, and `gpt` for GPT-2. 
For example, `zharry29/goal_benchmark_roberta` is the name for the RoBERTa model pretrained on the training data of the Goal Inference task. 

If you use our resources, please cite the following paper:
```
@inproceedings{zhang-etal-2020-reasoning,
    title = "Reasoning about Goals, Steps, and Temporal Ordering with {W}iki{H}ow",
    author = "Zhang, Li  and
      Lyu, Qing  and
      Callison-Burch, Chris",
    booktitle = "Proceedings of the 2020 Conference on Empirical Methods in Natural Language Processing (EMNLP)",
    month = nov,
    year = "2020",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://www.aclweb.org/anthology/2020.emnlp-main.374",
    pages = "4630--4639",
}
```
