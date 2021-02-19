---
title: "Making Tests"
date: 2020-10-12T18:34:25-07:00
weight: 910
---
## About the ModernApps Ninja Testing Service

This course template includes an automated test grading service, which works in concert with the completion certificate service to allow participants to earn a certificate of completion for the course.

It is important that test creators follow these instructions carefully, or the testing and completion certificate services will not work properly.

The testing service currently supports multiple choice single answer (MSMA) and multiple choice multiple answer (MSMA) type questions.

## Instructions

### Creating Tests

Tests are standard pages that you create the same as you would any other page on this site. When course participants take the test, they will submit their anwers on a seperate form, so there is no need to include any special input logic to enter answers on your test page.

The name of the page where test questions are presented does not matter, but the name of the answer sheet that students will use to submit answers to test questions will be titled `Test1.yml, Test2.yml, Test3.yml etc ...` where `Test1.yml` would be the first test in the standard sequence of pages as displayed on the course website. This order is determined by the `weight` property in the front matter of each page as noted in the [docsy template documentation](https://docsy.dev).

As a reference, please see the example [Test1 on the new course template repository](https://modernapps.ninja/$course_repo_name/docs/thebigpicture/test1/) 

We strongly recommend using the reference test linked above as a template for your test pages, in particular its important to include clear instructions to participants for how to submit answer responses on every test page, as shown in the reference test.

You can present your test questions in your preferred format, with the following requirements:

#### Required Question Naming/Numbering Format

All questions must follow a standard naming convention, The word `Question` followed by a whole integer starting with `1`, for example, `Question1, Question2, Question3 etc ...`

#### Required answer response format

All answers should be presented such that a single lowercase letter will represent each acceptable response. On a mutliple choice question, the first possible response should be represented by the letter `a`, the second possible response as `b`, the third as `c` and so on. Further detail on this format can be seen in the example questions below. 

### Example Questions

#### Example Multiple Choice Single Answer Question

```
Question1: What value will the bash shell return when you enter the command `echo hello`?

Answers:
  a: banana
  b: hello
  c: apple
  d: shutdown commencing
```

The correct answer to Question1 is `b` as the command will return the value hello. 

On the participants answer sheet, they would fill in the value `b` for Question1, as shown in the following example:

```
Question1: b
Question2:
Question3:
```

#### Example Multiple Choice Multiple Answer Question

```
Question2: Which of the following are fruits? (Select 3)

Answers:
  a: banana
  b: hello
  c: apple
  d: shutdown commencing
  e: orange
```

**IMPORTANT**: When providing answers to multiple choice multiple answer questions, participant responses must be in alphabetical order. For example, the correct answer for Question2 above is `a,c,e`, in alphabetical order, with a comma between each answer. If the answer was provided as `a,e,c`, the grading service would mark the answer incorrect as the response values were not provided in alphabetical order.

Partially correct answers will be counted as incorrect, no partial credit is given.

Spaces do not need to be inerted between each value in the response, but the grading service will ignore spaces if present. 

On the answer sheet, the participant would fill in the value `a,c,e` for Question2, as shown in the following example:

```
Question1: b
Question2: a,c,e
Question3:
```

### Submitting your test answer key

Once you have prepared the test, you must submit a test answer key to enable automated grading. 

The answer key is the exact text of the answer sheet, with all of the correct answers filled in. When a participant submits their answer response sheet, it will be compared against the answer key to determine which answers are correct.

To submit an answer key you will first prepare an answer key file, then encode the file as a base64 string, and then submit the answer key issue ticket, as detailed in the steps below. 

#### Preparing your answer key 

The answer key is a simple text document in which the only text should be the question number and correct response for each question without any additional lines. 

The testing service uses an Ubuntu Linux host to process automated grading, so it is important that you prepare your answer key file on a Linux host or using a IDE or text editor that will save the file in standard Linux LF format. 

Open your preferred text editor and create an answer key file. The file should follow the same format as the following example:

```yml
Question1: a
Question2: b
Question3: c
Question4: a,b,c
Question5: d
Question6: d,e
```

Once you have added all of the questions and answers for the test, save the file. It does not matter what you name the file, but in the following example we will assume the file is saved as `test1key.yml`.

#### Encoding your answer key in base64

This example shows the accepted method of encoding your answer file from the bash cli on an Ubuntu host. If you use a different system or method to encode your file, please know that the file will be decoded and processed by an ubuntu host using the bash command `base64 -d`, so please ensure that the encoded string you submit is accurately decoded into your answer key file when decoded with the `base64 -d command. 

Enter the following commands to encode your answer file:

```bash
prompt$ cat test1key.yml 
Question1: a
Question2: b
Question3: c
Question4: a,b,c
Question5: d
Question6: d,e
prompt$ cat test1key.yml | base64 -w 0 > test1key.yml.base64
prompt$ cat test1key.yml.base64 
UXVlc3Rpb24xOiBhClF1ZXN0aW9uMjogYgpRdWVzdGlvbjM6IGMKUXVlc3Rpb240OiBhLGIsYwpRdWVzdGlvbjU6IGQKUXVlc3Rpb242OiBkLGU=
```
Take note of the final line of the above example output, which is your file encoded in base64, you will need to use this string in the following steps.

If you would like to verify your answer key string, you can decode it and ensure that it accurately decodes into the identical file you created before encoding, as shown in the following example:

```bash
prompt$ cat test1key.yml.base64 | base64 -d
Question1: a
Question2: b
Question3: c
Question4: a,b,c
Question5: d
Question6: d,e
```

#### Initiate a "Submit a Test Answer Key" Workflow

When you are ready to publish a test, navigate to the github actions page for this course repository, and initiate a `Submit a Test Answer Key` Workflow.

1. In the Title field, enter the tests title, which is the word `Title` followed by the number of the test in the standard sequence of pages in the course, for example `Title1`, `Title2` etc. Do not include any other text or spaces, only the title.

2. In the Answer Key String field, enter the your answer key encoded as a base64 string. 

After you initiate the workflow:

- The workflow will verify that the github user submitting the answer key is part of the ModernApps Ninja Maintainers team
- The base64 encoded answer key string will be saved in a central datastore where it will be referenced each time a participant submits an answer sheet for grading.
- A new test answer sheet will be created and posted to this course repository in the `/static/admin/userdata/tests/`
- The workflow will open a discussion thread on the maintainers team page for the course, @mentioning the github user who initiated the worklow to provide information about the workflow run and a direct link to the new test answer response file. 

After you recieve the link to the answer response file for the test, please ensure that the page where you present test questions provides a link to the answer response file with clear instructions for the user. 

#### Additional Questions & Support

If you see any areas for improvement in this page, please click the `Edit this page` link on the right navigation bar and submit your recommended updates or improvements.

If you have any questions or need any assistance, please post a message to [new course discussion board](https://github.com/ModernAppsNinja/modernappsninja.github.io/discussions) and mention the `@modernappsninja/maintainers` team in the body of your message. Or you can also open an issue ticket on the [https://github.com/modernappsninja/modernappsninja.gitub.io](https://github.com/modernappsninja/modernappsninja.gitub.io) repository.