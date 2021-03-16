---
title: "Episode 3 Test"
date: 2020-10-09T03:15:26-07:00
weight: 4090
---

All Modernapps Ninja learning content is publicly accessible and available openly, however a free membership is required to take tests and recieve a certificate of completion for the course. You must first [join the community](https://modernapps.ninja/about/membership/) and register for this course per the instructions in the course introduction section before attempting to submit a test.

Ninja tests use devops tools and processes so the testing system itself provides both experience with and validation of foundational devops skills. 

- [Instructions](#instructions)
  - [Full Test Instructions](#full-test-instructions)
  - [Test Answer Response Sheet](#test-answer-response-sheet)
  - [Episode 3 Test Questions](#episode-3-test-questions)
      - [This concludes the episode 3 test. Please use the navigation bar to proceed to the next page.](#this-concludes-the-episode-3-test-please-use-the-navigation-bar-to-proceed-to-the-next-page)

## Instructions

This test uses automated grading, you must follow the instructions exactly to ensure automated grading will complete successfully. 

To complete the test you must review the questions on this page, and fill in your answers on a seperate answer sheet provided below. We recommend opening the answer sheet for the test in a seperate browser tab so you can fill in the answers as you proceed through the questions. 

Every question in this test is titled "Question" followed by its order, for example Question1, Question2 etc...

All questions will provide a list of possible answers. Each possible answer is represented by a lowercase letter, the first response is option "a", the second is option "b" and so on, as shown in the example questions below. 

The Answer sheet will open in Github's web-based editor, similar to the image shown below:

![Example Test Response Sheet](/vSphereTanzu301_vt4163/admin/assets/images/blank_test_screen_example.png)  

After you fill in your answer sheet, you will submit your responses as a git [pull request](https://docs.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests) following the instructions provided below, which will trigger a workflow that will grade your responses and provide your test grading sheet. 

### Full Test Instructions

If this is the first test you have taken, or if you have an questions at all about how to propely complete the test answer sheet or the test grading service, please review the full [How to Take a Test Instructions](https://modernapps.ninja/course_repo_template_ct8279/docs/reference/testinstructions/).  

It is important that you follow the instructions carefully to ensure the automated grading process completes successfully.

### Test Answer Response Sheet

Please right click the following link to the test answer response sheet and select to open it in a new tab. The questions for this test will be provided below in this page, but you will need to enter your responses in the answer response sheet. 

[test3 Answer Response Sheet](https://github.com/modernappsninja/vSphereTanzu301_vt4163/edit/main/static/admin/userdata/tests/test3.yml)  

### Episode 3 Test Questions

#### **Question1:** in a vSphere with Tanzu implementation that uses vDS and HAproxy, which of the following IP ranges should be prepared for the supervisor cluster networking topology?  <!-- omit in toc -->

**Please select the best 2 responses from the following:**

```yml
Answers:
  a: A range for allocating virtual IPs for HAProxy. The IP range that you configure for the virtual servers of HAProxy are reserved by the load balancer appliance. 
  b: DHCP IP ranges
  c: Configure a gateway within the HAProxy virtual IP range, so all routes to that gateway will succeed.
  d: An IP range for the nodes of the Supervisor Cluster and Tanzu Kubernetes clusters.
```

#### **Question2:** True or False - Before installing Workload Management (the user interface designation for running Kubernetes inside vSphere), you have to setup HA-Proxy, a virtual appliance for provisioning load-balancers. <!-- omit in toc -->

**Important: On your answer sheet, please use the letter a for true, and the letter b for false. DO NOT type in the words true or false on the answer sheet as the grading service only processes single letter responses**

```yml
Answers:
  a: true
  b: false
```

#### **Question3:** Kubernetes cluster configuration includes providing a CIDR range for Kubernetes services and a CIDR range for pods. || Select all that apply.: <!-- omit in toc -->

**Select 2 of the following statements:**

```yml
Answers:
  a: CIDR Range == IP Range. You can pick any IP range you want but it must not conflict with anything else on the management or workload networks.
  b: IP ranges are not needed for the supervisor cluster
  c: a /20 is required
  d: default for services is a /24 as supervisor cluster doesn't use a lot ... but this can be changed.
```


##### This concludes the episode 3 test. Please use the navigation bar to proceed to the next page.
