# TryoCoQA

A Conversational Question Answering dataset for Tryolabs' blogposts.

## Format

The dataset's format is almost identical to [CoQA's](https://stanfordnlp.github.io/coqa/). An example conversation has the following structure:

```
{
  "conversation_id": 0,
  "context_id": 0,
  "story": "Here's the full text content of one of Tryolabs' blogpost",
  "questions": [
    "What is a QA dataset?",
    "What is TryoCoQA?"
  ],
  "answers": {
    "input_text": [
      "A QA dataset is...",
      "TryoCoQA is a ...",
    ]
  }
}
```

## Versions

### TryoCoQA_v1

The first version of the dataset contains 15 conversations built from ~10 turns (question and answer pair) each. The conversations refer to 5 different blogposts, 3 conversations each. Here's the list of blogposts that were used and their corresponding `context_id`.

| `context_id`      | Blogpost URL |
| ----------- | ----------- | 
| 0      | [A guide to optimizing Transformer-based models for faster inference](https://tryolabs.com/blog/2022/11/24/transformer-based-model-for-faster-inference)       | 
| 1   | [Machine Learning 101: Build, Train, Test, Rinse & Repeat](https://tryolabs.com/blog/2022/09/22/machine-learning-101)        | 
| 2   | [Price optimization for e-commerce: a case study](https://tryolabs.com/blog/2020/06/01/price-optimization-for-e-commerce-a-case-study)        | 
| 3   | [Automatically measuring soccer ball possession with AI and video analytics](https://tryolabs.com/blog/2022/10/17/measuring-soccer-ball-possession-ai-video-analytics)        | 
| 4   | [Becoming an AI organization](https://tryolabs.com/blog/2021/11/10/becoming-an-ai-organization)        | 

## Strategy

Each conversation is assigned a Questioner and an Answerer. The Questioner asks the questions and decides when the conversations is over, and the Answerer responds to the questions. Questioner and Answerer are interchanged for each conversation. Instead of having just one labeller design both questions and answers, we hope this approach produces more natural conversations.

## Guidelines

The following tips were extracted from the [CoQA original paper](https://arxiv.org/pdf/1808.07042.pdf) and [Practical Annotation Strategies for Question Answering Datasets](https://arxiv.org/pdf/2003.03235.pdf).

### Questions

* Phrase the questions in natural language. Don't try to use the exact same words or order of words for building the questions. Use synonyms and change the word order.
* Think of questions that can be answered by the document at hand without any other information needed.
* You can ask yes/no questions but try to keep it at a minimum. They shouldn't exceed 20% of the dataset.
* Diversify the questions you ask and try to make many of them difficult. Ask the answerer for counts, summaries, comparisons, listings, rankings and more. With this in mind, simple questions are also welcomed.
* Make references to previous questions and/or answers to keep the conversation flowing. Try not to reference questions/answers that are far in time on the conversation.
* If a question has more than one answer, you can repeat it at any point in the conversation.
* Try not to repeat questions (even across conversations), unless these questions have multiple answers.
* The conversation should flow through the whole text. Try not to always start the questions from the beggining of the document or maybe not follow a straight line from beggining to end. Nonetheless, a conversation should try to cover as much of the blogpost as possible.
* You can ask unanswerable questions (for example, questions to which the answer can't be determined by the context). Try not to make too many unanswerable questions.

### Answers

* Keep answers as short as possible
* Try to use the same vocabulary as in the context. Don't use other words. You can change the order of words or sentences from different places of the context, but try to always use the same vocabulary (unless you are explicitly asked to do so; e.g. "Please, rephrase the last answer").
* If asked an unanswerable question, try to respond always with the same answer. For example, "I can't answer that."
* If a questions is repeated, try to give a different answer.

