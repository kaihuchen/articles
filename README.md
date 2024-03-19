<banner class="page-header" role="banner">
  <img src="assets/images/books.png" alt="Banner Image">
</banner>

# List of GenAI Articles, Code Repositories, and Apps

<a name="ensemble"></a>

**Ensemble GenAI**

<!-- <div style=“float: left”> !Image description </div> -->
- [**Wood vs Buffett on NVDA**](https://kaihuchen.github.io/articles/WoodvsBuffett/): An emulated debate between Cathie Wood and Warren Buffett on NVDA, as imagined by GenAI chatbots. Also with business models as suggested by chatbots. \
    *Published: Feb 26, 2024*
- [**Qualitative Financial Risk Assessment using Collective AI Judgement**](https://kaihuchen.github.io/articles/Risks): having multiple GenAI chatbots engage in a debate to derive a qualitative assessment of financial risk in regard to a certain given major event. \
    *Published: Feb 18, 2024*
- [**A Message from GenAI Chatbots to GenAI Startups**](/TheDebate): find out how two leading GenAI chatbots debate about the future of GenAI startups. \
    *Published: Feb 15, 2024*
- [Ensemble AI](EnsembleAI):（draft) making many heterogeneous chatbots work together, distributed, at global scale.\
*Unpublished*

<a name="enterprise"></a>

**GenAI for the Enterprises**

- [**Brainstorming with Chatbots on building a Universal Information Worker Chatbot**](https://kaihuchen.github.io/articles/Brainstorming/): How to use an ensemble of debating chatbot to design and implement a Universal Information Worker chatbot for enterprises. \
    *Published: March 14, 2024*

- [**The Manchurian Chatbot Problem: Are Chatbot Viruses Coming Our Way?**](https://kaihuchen.github.io/articles/ManchurianCandidate): Large Language Model (LLM) chatbots are becoming more advanced, but this progress could also lead to the "Manchurian Candidate" problem: the risk of adversaries implanting malicious data into LLMs' long-term memories, which could be triggered to cause harm. \
    *Published: March 12, 2024*

- [**Building Enterprise GenAI Chatbots**](EnterpriseBots): It is important to recognize that enterprise GenAI chatbots are essentially the latest iteration of traditional enterprise software applications. As such, many of the same challenges faced during their development cycles should not be overlooked or underestimated. \
    *Published: Feb 27, 2024*

**GenAI Vision Applications**

- [**Navigating the Pitfalls of Vision Language Models**](https://kaihuchen.github.io/articles/LMMissues):
this is a story about how a winning Claude-3 lose an image classification debate to GPT-4V, due to its weak personality. It is also about a cougar on house deck, and how AI ecould mistaken it as just a dog.\
    *Published: March 18, 2024*

- [**Is Anthropic's Claude-3 Ready for AGI?**](https://kaihuchen.github.io/articles/VisualCommonSenseClaude3): Does Anthropic's multimodal Claude-3 have enough visual common sense to support AGI (Artificial General Intelligence)? It is actually kind of close.

    *Published: March 4, 2024*

- [**Is OpenAI's GPT-4V Ready for AGI?**](https://kaihuchen.github.io/articles/VisualCommonSense): Does OpenAI's vision model GPT-4V have enough visual common sense to support AGI (Artificial General Intelligence)? It is actually kind of close.

    We ran 17 types of visual common sense tests against GPT-4V to find out how well it can deal with the real world, and here are the results.

    *Published: Feb 29, 2024*
- [**LMM for Level 5 Autonomous Driving**](https://github.com/kaihuchen/AutonomousBackseatDriver/blob/main/README.md): testing out the potential of using LMM (Large Multimodal Models) under the scenario of Level 5 autonomous driving, demonstrating LMM's capabilities in visual recognition, scene analysis, commonsense responses, and explanation. \
    *Published: Feb 2024*
- [LMM for a Home GuandianBot](https://github.com/kaihuchen/GuardianBot/blob/main/README.md): (draft) testing out the potential of using LMM (Large Multimodal Models) under the scenario of a home robot for detecting any hazards or threats, taking actions or escalating alerts as appropriate.\
*Unpublished*
- (Upcoming) Is OpenAI's GPT-4V vision model sufficient to support AGI?

**Hidden Problems in GenAI**

- [**Hallucination due to flawed Abductive Reasoning**](Bugs/#abductiveReasoning): My experiments show that most chatbots built from LLMs (Large Language Models) struggle with abductive reasoning, which often leading to incorrect or "hallucinated" responses that aren't easy to spot. \
    *Published: Feb 24, 2024*

# Source Code Repositories

- **Ensemble GenAI**\
*Not yet published*

# Apps

- Online apps
    - OpenAI GPTs Store (*an OpenAI account is needed to access*)
        - [Creative Imaginator](https://chat.openai.com/g/g-UpQkvuX7j-creative-imaginator): upload an image, select one of many predefined style, and the app automatically generate a new image that is different from the original in creative ways, but still follow the main theme in the original image. 

            This is basically an image-to-text-to-image tool with support for style injection, which is easier to manage than text-to-image system (which requires substantial prompt engieering skill), or the image-to-image approach (which is best for making small changes).

            This tool is ideal for anyone who just need to have some illustrations. A [gallery](https://github.com/FonchinChen/Creative-Imaginator/blob/main/README.md) is available here for viewing.
        - [Automatic Backseat Driver](https://chat.openai.com/g/g-e4IV3KhGm-autonomous-backseat-driver): upload a road scene, and have the scene analyzed in detail along with the recommended high-level action of whether to proceed, stop, or turn around. 
            
            This is a tool to test how well OpenAI's vision model GPT-4V can be used as a high-level component for driving a Level 5 Autonomous Vehicle.

            See [this gallery](https://github.com/kaihuchen/AutonomousBackseatDriver) for a long list of road scenes tested with this tool, which demonstrated that GPT-4V has performed surprising well even in highly challenging situations. 
        - Radiologist V2: 


# Additional Resources

- We welcome your comments or issue reports here: https://github.com/kaihuchen/articles/issues