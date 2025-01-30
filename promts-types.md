## Zero-Shot Learning

With zero-shot learning, you include the instructions but exclude verbatim completions. Zero-shot prompts rely on the model's existing knowledge to generate a response. Zero-shot prompts are useful when you want a general answer or when the task is straightforward and doesn't require much guidance. Zero-shot prompting is also less resource-intensive since it relies on existing knowledge.

Here's an example of a zero-shot prompt that tells the model to evaluate user input, determine the user's intent, and preface the output with "Intent: "

``` C#
string prompt = $"""
Instructions: What is the intent of this request?
If you don't know the intent, don't guess; instead respond with "Unknown".
Choices: SendEmail, SendMessage, CompleteTask, CreateDocument, Unknown.
User Input: {request}
Intent: 
""";
```

## Few shot learning

With few-shot learning, you include verbatim completions in your prompt to help guide the model's response. Typically one to five examples are included. The examples demonstrate the structure, style, or type of response you want. Few-shot learning produces more tokens and also causes the model to update its knowledge. Few-shot prompting is especially valuable for reducing ambiguity and aligning results with the desired outcome.

Here's an example of a few-shot prompt that tells the model to evaluate user input, determine the user's intent, and preface the output with "Intent: ".
```C#
string prompt = $"""
Instructions: What is the intent of this request?
If you don't know the intent, don't guess; instead respond with "Unknown".
Choices: SendEmail, SendMessage, CompleteTask, CreateDocument, Unknown.

User Input: Can you send a very quick approval to the marketing team?
Intent: SendMessage

User Input: Can you send the full update to the marketing team?
Intent: SendEmail

User Input: {request}
Intent:
""";
````

## personas in prompts

Assigning personas in prompts is a technique used to guide the model to adopt a specific point of view, tone, or expertise when generating responses. Personas allow you to tailor the output to better suit the context or audience of the task. This is useful when you need the response to simulate a profession or reflect a tone of voice. To assign a persona, you should clearly describe the role definition in your prompt.

Here's an example of a prompt that assigns a persona:

``` C#
string prompt = $"""
You are a highly experienced software engineer. Explain the concept of asynchronous programming to a beginner.
""";
```

## Chain of thought prompting

With chain of thought prompting, you prompt the model to perform a task step-by-step and to present each step and its result in order in the output. This can simplify prompt engineering by offloading some execution planning to the model, and makes it easier to isolate any problems to a specific step so you know where to focus further efforts. You can instruct the model to include its chain of thought, or you can use examples to show the model how to break down tasks.

Here's an example that instructs the model to describe the step-by-step reasoning:

``` C#
prompt = $"""
Instructions: A farmer has 150 apples and wants to sell them in baskets. Each basket can hold 12 apples. If any apples remain after filling as many baskets as possible, the farmer will eat them. How many apples will the farmer eat?

First, calculate how many full baskets the farmer can make by dividing the total apples by the apples per basket:
1. 

Next, subtract the number of apples used in the baskets from the total number of apples to find the remainder: 
1.

"Finally, the farmer will eat the remaining apples:
1.
""";
````
