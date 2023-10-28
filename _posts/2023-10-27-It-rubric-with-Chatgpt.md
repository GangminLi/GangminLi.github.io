---
title: "Generate a course assessement rubric using ChatGPT"
style: app
date: 2023-10-27 10:12:20

author_profile: true
toc: true
toc_label: "Page Content"


tags:
  - ChatGPT
  - Prompt Engineering
  - AI
  - Rubric
  - Teach
  - Education
  - Course assessment


header:
  teaser: "/assets/posts/rubric/rubric-teaser.png"
---

![title](/assets/posts/rubric/rubric.png)


# What is rubric?
This is what the bing tells me. A rubric is a tool used to evaluate or grade an assignment or task. It is a set of instructions or rules that articulate the expectations for assignments and performance tasks by listing criteria, and for each criteria, describing levels of quality. Rubrics contain four essential features: 
![perspective](/assets/posts/rubric/rubric-des.png)
1. a task description or a descriptive title of the task students are expected to produce or perform; 
2. a scale (and scoring) that describes the level of mastery; 
3. components/dimensions students are to attend to in completing the assignment/tasks; and 
4. description of the performance quality (performance descriptor) of the components/dimensions at each level of mastery.
Rubrics can be used for any assignment in a course, or for any way in which you ask students to demonstrate what they’ve learned. They can also be used to facilitate self and peer-reviews of student work. Rubrics can be analytic or holistic. An analytic rubric articulates different dimensions of performance and provides ratings for each dimension. A holistic rubric describes the overall characteristics of a performance and provides a single score.

# How Can ChatGPT Help Build Rubrics?
ChatGPT is a powerful AI language model that has the capacity to complete a multitude of tasks based on human prompts. With regards to rubrics, if we provide ChatGPT with the necessary information in a clear, detailed, and defined prompt, this AI can assist in quickly developing a well-crafted rubric aligned with learning objectives. 

# My prompt for Generating Rubrics
Take on the role of an experienced [university level 6 information technology course instructor].
Create a well-crafted and clear evaluation rubric for students in the form of a table using student-friendly language. The rubric is for the following student task description in the brackets:
[For the university level 6, that is the final year of a 4-year undergraduate program, a course named “advanced information technology”, you have been provided with an IT system use case, based on that case, you need to submit an individual report that based on the expectations taught and reviewed in class and outlined in this rubric, which will be used to evaluate your report. You may use the example attached for reference as an exemplar.] 

The rubric should contain three parts: Scoring and Scale, Criteria, and Descriptors.
The rubric should be fully aligned with the following curricular standards:

1. The report should be written in a formal report style for an academic as well as industrial audience.
2. Introduce the given use case with a personal and specific understanding and some critical analysis. This understanding should form the functional requirements for an IT solution that addresses the needs of the use case. 
3. The report should discuss three possible solutions how each works and the pros and cons with respect to the functional requirements.
4. One recommended solution should be provided based on the comparison of match and satisfaction to the use case
5. Provide a justification for your recommendation based on other factors like budget that is not functional
6. Provide a concluding statement or section that follows from and supports the recommendation presented.
7. Demonstrate command of the conventions of standard English grammar and usage when writing or speaking.
8. Demonstrate command of the conventions of standard English capitalization, punctuation, and spelling when writing in academic writing.

Use the following scoring scale for the rubric:
- Dissatisfacory  (35 points)
- Acceptable (45 points)
- Expected  (55 points)
- Moderate (65 points) 
- Exemplary (75 points)

Include the following criteria for each element of the scoring scale I just mentioned above:
- Use case analysis
- Solutions’ description
- Recommendation
- Justification
- Report Conventions

For each of the criteria and each scoring scale, generate a descriptor based on the standards I have provided.
Generate the rubric in the form of a table. The first row heading for the table should include the scoring scale and points. The first column on the left of the table should display the criteria. The descriptors for each component and score should be listed under the correct scoring scale and points column and criteria row. Make the descriptors in the table as specific to the standards as possible.

# The result

This is the result from ChatGPT.

![result](/assets/posts/rubric/Screenshot.png)

You can generate multiple results to do a comparision, until you are satisfied.
<p>
{% include  share.html %}
</p>

<span style="color:#9e9696"><i> Last updated: 20/10/2023</i> </span>

<p>
{% include  license.html %}
</p>