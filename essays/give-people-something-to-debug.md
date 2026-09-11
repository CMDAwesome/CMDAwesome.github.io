---
layout: essay
type: essay
title: "Give People Something to Debug"
date: 2026-09-10
published: true
labels:
  - Software Engineering
  - Communication
  - Stack Overflow
---

## Keep the frustration level down

Asking smart questions matters for a practical reason: I want an answer that actually helps. Investigating first might solve the problem before I even need to ask. If it does not, it helps me explain what happened, what I expected, and what I already tried. That saves time and keeps frustration down for everyone involved.

[Eric S. Raymond and Rick Moen's guide to asking questions](https://www.catb.org/~esr/faqs/smart-questions.html) emphasizes preparation, specific descriptions, and useful evidence. In programming, that means sharing relevant code, exact errors, and the input that triggers the problem. A huge code dump can still hide the issue. Even an AI cannot reliably figure out what I mean from nine vague words without background information.

![A focused question provides code, observations, and prior attempts, helping an answerer investigate. A vague question requires clarification first.]({{ '/img/question-context.svg' | relative_url }})

*Illustration created with AI assistance for this essay.*

## A question worth investigating

GManNickG's [question about sorted and unsorted arrays](https://stackoverflow.com/questions/11227809) gives answerers something concrete to investigate. The developer's program adds numbers to a total when they are at least 128. This is the central condition, excerpted from the question:

```cpp
if (data[c] >= 128)
    sum += data[c];
```

The surprising part was performance: the loop took approximately 11.54 seconds with unsorted data but only 1.93 seconds after sorting. The developer supplied a runnable example and tried Java too, finding similar behavior.

To me, that preparation makes the question interesting and potentially fun to answer. Someone knowledgeable can focus on explaining the result instead of first asking what the program does. It follows Raymond's guidance by providing a specific problem, measurements, and evidence of investigation. The developer also distinguishes observations from possible explanations instead of treating a guess as a fact.

Mysticial posted an answer five minutes later. Its expanded version explains branch prediction: the processor predicts which way a condition will go, and sorted numbers make that pattern easier to predict. It also includes alternative code and benchmarks. The answer has been edited since its initial posting, so all that detail did not necessarily arrive in five minutes. Still, the discussion shows how a focused question supports a useful technical explanation.

## One line leaves too many possibilities

Raymond Pittman's [null-pointer exception question](https://stackoverflow.com/questions/16780588) provides one line containing several method calls and asks what the exception means and how to fix it. The post does not include a stack trace, surrounding initialization code, or debugging attempts. Here is the supplied line, reformatted for readability:

```java
if (methodCall.getClassName(cg.getConstantPool())
    .contains(ALLATORI_CLASS.getClassName())) {
```

A null-pointer exception can occur when code tries to use a reference that does not point to an object. Several references in this expression could be responsible. The overall request is understandable, but the information needed to identify the particular failure is missing.

This falls short of Raymond's advice to provide precise diagnostic details. Comments ask for a stack trace and suggest separating the method calls. Mike Samuel explains several possible causes and recommends logging. Another answer says the single line is insufficient for further help. Responses arrived quickly, but the visible discussion establishes no verified fix.

My first reaction was frustration: why make someone ask another question before they can answer yours? However, an incomplete post does not prove that the developer does not care. They may not know which details matter. The practical issue is that missing context creates extra work, regardless of the person's intentions.

## What I would do differently

These examples do not prove that smart questions always get better answers. They do show me what makes a question easier to work with. I would copy the first developer's habit of providing evidence and comparing behavior. For the second question, I would include the stack trace, relevant initialization code, and the results of checking which references were null.

My main takeaway is that asking for help is part of debugging. Sharing observations and explaining what I tried lets someone more experienced notice connections I missed. I do not need to know the answer before asking, but I should give the other person enough information to make progress.

## AI assistance disclosure

I used ChatGPT to find and explain the Stack Overflow examples and help organize, draft, and revise this essay. I provided my own reactions and main arguments, which ChatGPT helped turn into a structured draft. ChatGPT also created the illustration and helped publish the essay.
