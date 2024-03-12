<banner class="page-header" role="banner">
  <img src="../assets/images/brainstorming.webp" alt="Banner Image" style="">
</banner>

# Brainstorming with Bots on Universal Information Worker

*Last updated: March 12, 2024*

This is a work log that serves the following purposes:

- This is a technical design document regarding how to implement a Universal Information Worker (UIW) for the enterprises. The motivation for UIW can be found [HERE](https://www.linkedin.com/posts/kaihuchen_title-building-a-genai-based-universal-information-activity-7173027315751333888-nGuM/?utm_source=share&utm_medium=member_desktop).
- This is also meant as a test ground for implementing a substantial GenAI enterprise software with the help of chatbots, from brainstorming to actual implementation. 
- This is also a test ground for the *Ensemble GenAI* idea, where a panel of debating chatbots are used to work together under the *constructive critique* process in order to hash out an answer to the question at hand.

  Here are some relevant articles that demonstrate the process:

  - [**Wood vs Buffett on NVDA**](WoodvsBuffett): An emulated debate between Cathie Wood and Warren Buffett on NVDA, as imagined by GenAI chatbots. Also with business models as suggested by chatbots.
  - [**Qualitative Financial Risk Assessment using Collective AI Judgement**](Risks)：having multiple GenAI chatbots engage in a debate to derive a qualitative assessment of financial risk in regard to a certain given major event.
  - [**A Message from GenAI Chatbots to GenAI Startups**](TheDebate): find out how two leading GenAI chatbots debate about the future of GenAI startups.

<a name='worklog'></a>

## Work Log

The entries below are listed in *reverse chronological* order
- 2024.03.12 Initial content

## Index of Contents

- Finding a good name
- [The overall setup of this experiment](#setup)

<a name='setup'></a>

## The Setup


A panel of GenAI chatbots are used to help us flesh out the design process from end to end. 

- The following LLMs for their robust text and vision capabilities:
  - OpenAI gpt-4
  - Anthropic Claude-3-opus-20240229
- Each LLM is accessed through Python Langchain's ConversationChain class
- For each given query, the debate among the chatbots take place in three rounds:
  - Round 1: Opinion Presentation. Each chatbot expresses its opinions regarding the given query
  - Round 2: Analysis and Critique. Each chatbot expresses its cretiques regarding the opinions given by other chatbots in round 1. Each chatbot also assign each critique with a score on a 1-10 scale.
  - Round 3: Resolution and Synthesis. Each chatbot tries to reconcile opponent's opinions with its own to create a synthesized opinion. Issues that cannot be reconciled are listed separately.
- Unless noted otherwise, all prompts are given to a panel of two chatbots
- Unless noted otherwise, only the reconciled round-3 results are presented so that this article does not get excessively long. The lists given in round 3 may also get truncated if it gets too long.


## Finding a good name

**Prompt to the chatbot panel**: I am building a GenAI chatbot intended for use by enterprises. This chatbot behaves like an individual worker with the ability to operate any existing software GUI intended for human workers, and it is able to communicate in natural language, solve problems, create contents, and work with human or chatbot colleagues in a team in order to complete the assigned task. Please come up with some catchy names to describe this system.
<!-- I am building a system that employs a panel (or ensemble) of GenAI chatbots to debate each other in order to get things done. Please come up with some catchy names to describe this system. -->

**Round #3: Resolution and Synthesized Opinions**

    Participant: #1:openai_gpt-4
        
        Here are the reconciled opinions in descending order of scores:
        
        1. OmniWorkerAI (Score: 8)
          - Comprehensive and straightforward name suggesting an AI that can handle various tasks.
        
        2. OmniTasker (Score: 8)
          - Simple and clear name suggesting a product that can handle various tasks.
        
        3. GeniusWorkerAI (Score: 8)
          - Catchy and creative name suggesting an AI that works smartly.
        
        4. IntelliWorkerBot (Score: 8)
          - Simple and clear name suggesting a bot that works intelligently.
        
        5. WorkWiseBot (Score: 8)
          - Catchy and straightforward name suggesting a bot that works wisely.
        
        6. GeniusTasker (Score: 8)
          - Creative and straightforward name suggesting a product that can smartly handle tasks.
        
        7. TaskWhizBot (Score: 8)
          - Catchy and straightforward name suggesting a bot that's a whiz at tasks.
        
        8. TaskMavenAI (Score: 8)
          - Catchy and straightforward name suggesting an AI that's an expert at tasks.
        
        9. WorkGuruBot (Score: 8)
          - Catchy and straightforward name suggesting a bot that's a guru at work.
        
        10. OmniAssist (Score: 8)
            - Professional and trustworthy name conveying the all-encompassing assistance capabilities of the chatbot.
        
        11. TaskMasterBot (Score: 7)
            - Easy to pronounce but lacks creativity, suggesting a bot designed to master tasks.
        
        12. WorkFlowMasterAI (Score: 7)
            - Descriptive but a bit long, suggesting an AI that can master workflow.
        
        13. OmniMateAI (Score: 7)
            - Simple but not very creative, suggesting an AI that can be a mate in various tasks.
        
        14. AllRounderBot (Score: 7)
            - Simple and clear name suggesting a bot that can handle various tasks.
        
        15. TaskMagnetAI (Score: 7)
            - Catchy but may not clearly indicate what the AI does, suggesting an AI that attracts tasks.
        
        16. WorkSphereBot (Score: 7)
            - Straightforward but not very creative, suggesting a bot that encompasses all work.
        
        17. TaskUniverseAI (Score: 7)
            - Creative but a bit long, suggesting an AI that can handle all tasks.
        
        18. TaskMastermindAI (Score: 7)
            - Creative but a bit long, suggesting an AI that's a mastermind at tasks.
        
        19. WorkForceAI (Score: 7)
            - Straightforward but lacks creativity, suggesting an AI that can be a workforce.
        
        20. AdaptaBot (Score: 7)
            - Catchy and memorable, highlighting the chatbot's ability to adapt to various software and tasks.
        
        21. IntelliWorker (Score: 7)
            - Professional and suggests efficiency, focusing on the intelligent worker capabilities of the chatbot.
        
        Opinions that are irreconcilable:
        
        1. TaskGenieAI (Score: 9)
          - Creative and catchy name suggesting an AI that can magically handle tasks.
        
        2. OmniTaskGenie (Score: 9)
          - Creative and catchy name suggesting a product that can magically handle various tasks.
        
        3. EnterpriseGenie (Score: 7)
          - Catchy but doesn't clearly indicate what it does, suggesting a product designed for enterprise use.
        
        4. EnterpriseMate (Score: 6)
          - Suggests a product designed for enterprise use but doesn't clearly indicate what it does.
        
        5. GenWorkAI (Score: 6)
          - Vague and doesn't clearly indicate what the AI does.
        
        6. UniTaskBot (Score: 6)
          - Suggests a bot that can handle a single task, which might limit its appeal.
        
        7. GUIversalBot (Score: 5)
          - Complex and could be hard to pronounce, doesn't clearly indicate what the bot does.
        
        8. SynthIA (Score: 6)
          - Clever play on words, emphasizing the artificial intelligence aspect of the chatbot, but might not

    Participant: #2:anthropic_claude-3-opus-20240229

        Reconciled Opinions in Descending Scores:
        
        1. TaskGenieAI - 8.5
        2. OmniTaskGenie - 8.5
        3. TaskMavenAI - 8.5
        4. OmniAssist - 8
        5. TaskMasterBot - 8
        6. OmniTasker - 8
        7. WorkFlowMasterAI - 8
        8. WorkWiseBot - 8
        9. EnterpriseGenie - 8
        10. TaskWhizBot - 8
        11. WorkForceAI - 8
        12. TaskMastermindAI - 8
        13. WorkGuruBot - 8
        14. OmniWorkerAI - 7.5
        15. TaskUniverseAI - 7.5
        16. AdaptaBot - 7
        17. UniTaskBot - 7
        18. GeniusWorkerAI - 7
        19. IntelliWorkerBot - 7
        20. IntelliWorker - 7
        21. OmniMateAI - 7
        22. GeniusTasker - 7
        23. AllRounderBot - 7
        24. WorkSphereBot - 7
        25. TaskMagnetAI - 6.5
        26. GenWorkAI - 6
        27. EnterpriseMate - 6
        28. SynthIA - 6
        29. NaturaLink - 6
        30. GUIversalBot - 5
        31. UniBot - 5
        32. VersaBot - 5
        33. SolveBot - 4
        34. TeamMate - 4
        35. CreatIO - 3
        36. SmartCollab - 3
        37. GeniusFlow - 2
        38. SynergAI - 2
        39. PolyBot - 2
        40. CogniCollab - 1
        
        Inreconcilable Opinions:
        None. The opinions from both sources were able to be combined without conflict.
        
**Decision**: Deferred


## Finding target application domains

**Prompt**: Imagine that you are an entrepreneur in generative AI, and you want to use a technology involving many GenAI chatbots to help with making important decision together in order to improve prediction accuracy and reliability. Please make brainstorming suggestions on which domains and what kind of applications might have a sizable market, that are suitable for the said technology. 

**Gemini**: Here's a brainstorm of domains and applications suitable for a decision-making system powered by collaborative generative AI chatbots, focusing on market potential:

  - Domains with Big Data, Complex Decisions, and High Stakes:

    - Finance:
        - Investment Analysis: Each chatbot could specialize in a different market sector, analysis style (fundamental, technical, etc.), or asset class. Their collective "wisdom," filtered through a decision engine, could offer more balanced investment recommendations.
        - Risk Management: Diverse chatbots trained on different risk models (credit, market, operational) could identify potential blind spots overlooked by traditional risk assessments.
        - Algorithmic Trading: Chatbots could generate new trading ideas or stress-test current strategies, potentially identifying unforeseen scenarios and enhancing optimization.

    - Healthcare:
        - Diagnosis and Treatment Planning: Chatbots trained on specific disease areas, medical literature, and anonymized patient data could suggest differential diagnoses or generate personalized treatment options, augmenting physicians' abilities.
        - Clinical Trial Optimization: Designing a robust clinical trial is complex. Chatbots could identify gaps in study designs, anticipate recruitment challenges, and suggest ways to streamline the process.
        - Medical Research: Analyzing vast amounts of research literature is labor-intensive. Chatbots could flag promising correlations, generate new hypotheses, or summarize vast bodies of research on specific topics.

    - Supply Chain Management:
        - Demand Forecasting: Chatbots could pull data from diverse sources like social media, weather patterns, and economic indicators to generate more accurate demand predictions, mitigating stockouts or oversupply.
        - Logistics Optimization: Routing, real-time traffic and disruption updates, and shipment consolidation could be enhanced by chatbots collaborating to propose the most efficient logistics solutions.
        - Supplier Analysis: AI bots could assess supplier capacity, risks (political, environmental), and compliance, adding context to traditional metrics for procurement decisions.

    - Government and Policy:
        - Policy Design: Chatbots could simulate the potential outcomes of different policy approaches, considering social, economic, and environmental impacts, helping officials make data-driven decisions.
        - Resource Allocation: Analyzing complex data sets on demographics, infrastructure, and needs could allow chatbots to recommend areas for focused funding or resource deployment.
        - Crisis Scenario Planning: Collaborating chatbots could rapidly analyze information during complex emergencies to propose evacuation routes, identify vulnerable populations, or predict cascading effects.

  - Key Considerations for Success:

    - Diversity of Data & Models: The strength of this approach lies in drawing from multiple perspectives. Training chatbots on different data sources and analytical models enhances decision-making.
    - Transparency and Explainability: To gain user trust, especially in high-stakes scenarios, the system must explain how it combined the outputs of the various chatbots and why it generated a particular recommendation.
    - Security and Bias: Careful attention must be paid to data security and protection against inherent biases in training data.
    - Human-in-the-loop Architecture: This isn't about replacing human judgment, but augmenting it. Experts should retain the final decision-making authority, informed by the collective intelligence of the chatbot system.


<!-- <banner class="page-header" role="banner">
  <img src="../assets/images/brainstorming.webp" alt="Banner Image">
</banner> -->
