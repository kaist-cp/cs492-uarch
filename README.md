# KAIST CS492: Microarchitecture Design

## Logistics

- Instructor: [Jeehoon Kang](https://cp.kaist.ac.kr/jeehoon.kang)
- Time: Mon & Wed 13:00-14:15 (2024 Fall)
- Place
  + Rm. 1101, Bldg. E3-1. **YOUR PHYSICAL ATTENDANCE IS REQUIRED** unless announced otherwise.
  + [Zoom room](https://kaist.zoom.us/my/jeehoon.kang) (if remote participation is absolutely necessary).
    Ask Jeehoon via email for the passcode.
- Websites: <https://github.com/kaist-cp/cs492-uarch>, <https://gg.kaist.ac.kr/course/21>
- Announcements: in the [issue tracker](https://github.com/kaist-cp/cs492-uarch/issues?q=is%3Aissue+is%3Aopen+label%3Aannouncement)
  + We assume that you will read each announcement within 24 hours.
  + We strongly recommend you watch the repository.
- TA: [Minseong Jang](https://cp.kaist.ac.kr/minseong.jang), [Jungin Rhee](https://cp.kaist.ac.kr/jungin.rhee)
  + Office Hours: Fri 9:00-10:00, Rm. 4441, Bldg. E3-1.
    If you want to come, do so by 9:15.
    See [below](https://github.com/kaist-cp/cs492-uarch#rules) for the office hour policy.
    <!-- Fri 9:00-12:00, [Zoom room](https://zoom.us/j/4842624821)(The passcode is same as the class). It is not required, but if you want to come, do so by 9:30. See [below](#communication) for office hour policy. -->
- **IMPORTANT**: you should not expose your work to others. In particular, you should not fork the [upstream](https://github.com/kaist-cp/cs492-uarch) and push there.


## Course Description

### Context

It is ["A Golden Age for Computer Architecture"](https://www.youtube.com/watch?v=aA5pqklkkvI), and also ["A Golden Age of Hardware Description Languages"](https://drops.dagstuhl.de/entities/document/10.4230/LIPIcs.SNAPL.2019.7).
The demand for a tremendous amount of computation necessitates the development of purpose-built, specialized hardware (also known as accelerators), and consequently, productive RTL design tools (such as hardware description languages or HDLs) for these accelerators.


### Goal

In this course, you will learn an opinionated RTL design process, specifically using "HazardFlow HDL", developed at the [KAIST Concurrency and Parallelism Laboratory](https://cp.kaist.ac.kr/hardware/).
HazardFlow HDL facilitates modular RTL design of pipelines even in the presence of hazards.
Unlike existing high-level HDL and high-level synthesis tools for similar purposes, HazardFlow HDL aims to provide predictable performance, power, and area (PPA) transparently to designers.
By understanding and developing designs in HazardFlow HDL, students are expected to build a modern and effective perspective on RTL designs.


### Textbook

- Lecture note ([Google Docs](https://docs.google.com/document/d/1VddAsurGBaMQRDUtRzxSSitqBwzwy6uKHVh0ZlJUI60/edit?usp=sharing))
- HazardFlow HDL User Guide ([mdBook](https://kaist-cp.github.io/hazardflow/book/))
- HazardFlow HDL Reference Manual ([rustdoc](https://kaist-cp.github.io/hazardflow/docs/hazardflow_designs/))


### Prerequisites

- It is **strongly recommended** that students have completed courses in:

    + Mathematics (MAS101)
    + Data Structures (CS206)
    + Programming Languages (CS320)
    + Computer Organization (CS311)

  A solid foundation in these areas is crucial for success in this course.

- It is **strongly recommended** that students can speak the [Rust programming language](https://www.rust-lang.org/).


### Schedule

- Week 01: Introduction
- Week 02: RTL and Verilog
- Week 03: RTL debugging
- Week 04: Modular RTL design (1/2)
- Week 05: Modular RTL design (2/2)
- Week 06: Pipelined RISC processor (1/3)
- Week 07: Pipelined RISC processor (2/3)
- Week 08: No class (midterm exam period)
- Week 09: Pipelined RISC processor (3/3)
- Week 10: AI accelerator (1/3)
- Week 11: AI accelerator (2/3)
- Week 12: AI accelerator (3/3)
- Week 13: RTL analysis tools
- Week 14: High-level synthesis
- Week 15: Invited talks
- Week 16: No class (final exam period)


### Tools

Ensure you are proficient with the following development tools:

- [Git](https://git-scm.com/): Essential for downloading homework templates and managing your development process.
  If you're new to Git, please complete [this tutorial](https://www.atlassian.com/git/tutorials).

    + Follow these steps to set up your repository:
        * Clone the upstream repository directly without forking it:
          ```bash
          $ git clone --origin upstream git@github.com:kaist-cp/cs492-uarch.git
          $ cd cs492-uarch
          $ git remote -v
          upstream	git@github.com:kaist-cp/cs492-uarch.git (fetch)
          upstream	git@github.com:kaist-cp/cs492-uarch.git (push)
          ```
        * To receive updates from the upstream, fetch and merge `upstream/main`:
          ```bash
          $ git fetch upstream
          $ git merge upstream/main
          ```

    + For managing your development on a Git server, create a private repository:
        * Upgrade to a "PRO" GitHub account, available at no cost.
          See the [documentation](https://education.github.com/students).
        * Configure your repository as a remote:
          ```bash
          $ git remote add origin git@github.com:<github-id>/cs492-uarch.git
          $ git remote -v
          origin	 git@github.com:<github-id>/cs492-uarch.git (fetch)
          origin	 git@github.com:<github-id>/cs492-uarch.git (push)
          upstream git@github.com:kaist-cp/cs492-uarch.git (fetch)
          upstream git@github.com:kaist-cp/cs492-uarch.git (push)
          ```
        * Push your work to your repository:
          ```bash
          $ git push -u origin main
          ```

- [Rust](https://www.rust-lang.org/): The HDL we will use is embedded in Rust.

- [Verilog](https://www.chipverify.com/tutorials/verilog): The Rust-embedded HDL we will use is compiled into Verilog. You need to be able to read Verilog code when debugging (e.g., analyzing waveforms).

- [ChatGPT](https://chat.openai.com/) or other Large Language Models (LLMs) (optional): Useful for completing your homework.
    + In an AI-driven era, learning to effectively utilize AI in programming is crucial.
      Homework difficulty is adjusted assuming the use of ChatGPT 3.5 or an equivalent tool.

- [Visual Studio Code](https://code.visualstudio.com/) (optional): Recommended for developing your homework, although you may use any editor of your preference.

- [Single Sign On (SSO)](https://auth.fearless.systems/): Use the following SSO credentials to access [gg](https://gg.kaist.ac.kr) and the [development server](https://cloud.fearless.systems):
    + id: KAIST student id (8-digit number)
    + email: KAIST email address (@kaist.ac.kr)
    + password: Reset it here: <https://auth.fearless.systems/if/flow/default-recovery-flow/>
    + Log in to [gg](https://gg.kaist.ac.kr) using the "kaist-cp-class" option, and to the [development server](https://cloud.fearless.systems) using the "OpenID Connect" option.

- [Development Server](https://cloud.fearless.systems/):
    + **IMPORTANT: Do not attempt to hack or overload the server. Please use it responsibly.**
    + Create and connect to a workspace to use the terminal or VSCode (after installation).
    + We recommend using VSCode with the "Rust Analyzer" and "CodeLLDB" plugins.


## Grading & Honor Code

### Cheating

**IMPORTANT: READ CAREFULLY. THIS IS A SERIOUS MATTER.**

- Sign the KAIST CS Honor Code for this semester.
  Failure to do so may lead to expulsion from the course.

- We will employ sophisticated tools to detect code plagiarism.
    + Search for "code plagiarism detector" on Google Images to understand how these tools can identify advanced forms of plagiarism.
      Do not attempt plagiarism in any form.

### Programming Assignments (100%)

- All assignments will be announced at the start of the semester.
- Submit your solutions to <https://gg.kaist.ac.kr/course/21>.
- You are **permitted** to use ChatGPT or other LLMs.

### Attendance (?%)

- A quiz must be completed on the [Course Management](https://gg.kaist.ac.kr/course/21) website for each session (if any).
  **Quizzes should be completed by the end of the day.**

- Failing to attend a significant number of sessions will result in an automatic grade of F.


## Communication

### Registration

- Ensure your ability to log into the [lab submission website](https://gg.kaist.ac.kr).
    + Use your `kaist-cp-class` account for login.
    + Your ID is your `@kaist.ac.kr` email address.
    + Reset your password here: [https://auth.fearless.systems/if/flow/default-recovery-flow/](https://auth.fearless.systems/if/flow/default-recovery-flow/)
    + Contact the instructor if login issues arise.

### Rules

- Course-related announcements and information will be posted on the [course website](https://github.com/kaist-cp/cs492-uarch) and the [GitHub issue tracker](https://github.com/kaist-cp/cs492-uarch/issues).
  It is expected that you read all announcements within 24 hours of their posting.
  Watching the repository is highly recommended for automatic email notifications of new announcements.

- Questions about course materials and assignments should be posted in [the course repository's issue tracker](https://github.com/kaist-cp/cs492-uarch/issues).
    + Avoid sending emails to the instructor or TAs regarding course materials and assignments.
    + Research your question using Google, Stack Overflow, and ChatGPT before posting.
    + Describe your question in detail, including:
        * Environment (OS, Rust version, and other relevant program information).
        * Used commands and their results, with logs formatted in code.
          See [this guide](https://guides.github.com/features/mastering-markdown/).
        * Any changes made to directories or files.
          For solution files, describe the modified code sections.
        * Your Google search results, including search terms and learned information.
    + Use a clear and descriptive title for your issue.
    + For further instructions, read [this section](https://github.com/kaist-cp/cs492-uarch#communication) on the course website.
    + The requirement to ask questions online first is twofold: It ensures clarity in your query and allows everyone to benefit from shared questions and answers.

- Email inquiries should be reserved for confidential or personal matters.
  Questions not adhering to this guideline (e.g., course material queries via email) will not be addressed.

- Office hours will not cover *new* questions.
  Check the issue tracker for similar questions before attending.
  If your question is not listed, post it as a new issue for discussion.
  Office hour discussions will focus on unresolved issues.

- Emails to the instructor or head TA should start with "CS492(uarch):" in the subject line, followed by a brief description.
  Include your name and student number in the email.
  Emails lacking this information (e.g., those without a student number) will not receive a response.

- If attending remotely via Zoom (https://kaist.zoom.us/my/jeehoon.kang), set your Zoom name to `<your student number> <your name>` (e.g., `20071163 강지훈`).
  Instructions for changing your Zoom name can be found [here](https://support.zoom.us/hc/en-us/articles/201363203-Customizing-your-profile).

- The course is conducted in English.
  However, you may ask questions in Korean, which will be translated into English.

## Ignore

1830eaed90e5986c75320daaf131bd3730b8575e866c4e92935a690e7c2a0718
