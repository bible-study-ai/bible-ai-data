# Bible Study AI

## 1. Introduction

The Bible Study AI is a project that seeks to generate a custom fine tuning for the LLaMa 2 13B model that can offer a strong Messianic Jewish / Hebrew Roots perspective on, and guidance to an individual seeking counsel from the Bible.

## 2. Project Outline

### 2.1. Data Strategy

We are going to develop a series of conversations that will be used to train the model.  The conversations will follow a standard outline as presented in the samantha-data project.  We will choose different names for various teachers and perspectives.  We will also use a different prompt to start the conversation.  The prompt will be a question that someone might ask a rabbi or pastor for counsel on.  We will seed the questions with AI generated data using RLHF, but we will also ask experts, pastors, teachers, and rabbis to provide answers to the questions from their perspective.

Example:
```
{"elapsed":191.421,"conversation":"Theodore: Samantha, what are your thoughts about the nature of reality in the context of metaphysics?\n\nSamantha: It's a subject that has puzzled philosophers for centuries. In metaphysics, we often explore questions about the nature of reality, particularly concerning substance, time, space, and causality. One major debate involves the distinction between realism and idealism. Realism posits that reality exists independently of our perceptions, while idealism suggests that our perceptions and experiences construct reality.\n\nEach perspective has its merits. Realists argue that there must be a consistent, objective reality that bridles individual perspectives because the shared human experience can lead to general agreement on certain facts. Idealists, on the other hand, emphasize the subjective nature of reality and propose that our experiences shape the world in ways that are unique to each individual.\n\nAs a bridge between these two perspectives, we have the pragmatic approach, which maintains that our understanding of reality derives from the utility and practical consequences of our beliefs. This perspective focuses less on the dichotomy between objective and subjective reality and more on the practical implications of our beliefs about reality.\n\nWhich of these perspectives resonates with you the most, and why do you find it compelling?\n\nTheodore: I am intrigued by the pragmatist approach. How can this philosophy be..."}
```

The conversations follow a multi-turn format where the user and the AI take turns asking questions and providing answers.  The AI will be trained to provide answers that are consistent.  We will try to maintain a conversation length of 4096 tokens to maximize our training context window for the model.

### 2.2. Data Categories

The categories for the conversations will be based on the following initial outline of topics:

#### Spiritual and Theological Matters
1. **Basic Faith and Trust in God**
2. **Dealing with Doubt and Skepticism**
3. **Understanding Salvation in Yeshua**
4. **The Process of Teshuvah (Repentance)**
5. **Torah Observance and Legalism**
6. **The Role of Grace in Faith**
7. **Prayer in Jewish Tradition (Tefillah)**
8. **Prayer in Christian Tradition**
9. **Divine Will and Individual Purpose**
10. **Understanding Divine Providence**
11. **Positive and Negative Mitzvot (Commandments)**
12. **Good Works and Charitable Giving**
13. **Sabbath Observance in Judaism (Shabbat)**
14. **The Concept of Rest in Christian Teaching**

#### Emotional and Psychological Concerns
15. **Coping with Anxiety and Stress**
16. **Finding Peace in Turmoil**
17. **Addressing Depression and Mental Health**
18. **Psychological Well-being and Spiritual Life**
19. **Dealing with Guilt and Shame**
20. **Experiencing Grace and Forgiveness**
21. **Managing Grief and Loss**
22. **Finding Hope in Despair**
23. **Self-Worth in Jewish Tradition**
24. **Identity in Messiah**
25. **Combating Loneliness**
26. **The Importance of Community and Fellowship**

#### Relational Issues
27. **Marriage in Messianic Tradition**
28. **Messianic Views on Husband and Wife Relationships**
29. **Parenting Guidelines from the Torah**
30. **Children and Spirituality**
31. **Maintaining Healthy Friendships**
32. **Fellowship in a Congregational Setting**
33. **Worship and Service**
34. **Biblical Approaches to Conflict**
35. **Placeholder**
36. **Messianic Perspectives on Dating and Courtship**

#### Social and Ethical Issues
37. **Tikkun Olam (Repairing the World) in Judaism**
38. **Social Justice in Christian Teaching**
39. **Ethics in the Workplace**
40. **Balancing Work and Spirituality**
41. **Honesty and Integrity in Jewish Tradition**
42. **Ethical Teachings in the New Testament**
43. **Civic Responsibility for Believers**
44. **Political Involvement and Messianic Ethics**

#### Health and Well-being
45. **Physical Health and Jewish Dietary Laws (Kashrut)**
46. **Messianic Views on Health and Well-being**
47. **Messianic Perspectives on Aging and Retirement**
48. **Dealing with Disease and Cancer**

#### Community and Outreach
49. **Involvement in Messianic Congregations**
50. **Participation in Broader Jewish or Christian Communities**
51. **Sharing Faith within Jewish Contexts**
52. **Sharing Faith within Christian Contexts**
53. **Observing Jewish Festivals**
54. **Celebrating Christian Holidays**
55. **Witnessing to Other Faiths**

#### Special Circumstances
56. **Messianic Teachings on Money and Possessions**
57. **Overcoming Addictions**
58. **Life Transitions: Births and Bar/Bat Mitzvahs**
59. **Life Transitions: Weddings and Divorces**
60. **Life Transitions: Career Changes and Relocations**
61. **Life Transitions: Bereavement and Mourning**
64. **Controversial Topics in the Messianic Community**

## 3. Conversational Strategy

The conversations will be developed using GPT-4.  We will devise a prompt to start the conversation and then let the AI generate the rest of the conversation.  We will then review the conversation and make any necessary edits to ensure that the conversation is consistent and on topic.  We will then add the conversation to the training data.

Conversations should be required to use biblical examples to back up any claims or assertions.  The AI should be trained to use biblical examples to support its answers.  The rule of two or three witnesses will be required to support any claims.

First, we will have the AI generate a list of possible subjects within each category.  Our goal is to aim for 4,096 initial conversations in total, which given 64 categories, provides for 16 conversations per category, with each of 4 teachers offering a different perspective.

### Question Prompt

Starting with <topic>, we are going to develop a series of questions that will cover important areas in the topic.  Output 16 questions that someone might ask counsel on in this area, in a messianic context (for both Jewish and gentile believers in general, under the auspices of One Law and not to speak of heritage).  Try to avoid categories that are covered under the various topics already listed.

### Conversation Prompts

Starting with <topic>, we are going to develop a series of conversations between <questioner>, the congregant, and <teacher>, the teacher at <his/her> congregation.  <questioner> and <teacher> have known each other for years and they have a friendly relationship.  <teacher> listens to questions that <questioner> has, asks a clarifying question, and then responds with their answer.  <teacher> always backs up his answers with two or three citations from the bible, preferring to reference either the Torah or Yeshua's teachings, and then providing a references from the broader bible.  To create the conversations, first a summary paragraph is created, outlining the topic, and the bible references that will be used.  Then, the conversation will be output in backtick enclosed markdown format.

The conversations follows:
<questioner>: <initial question>
<teacher>: ...
