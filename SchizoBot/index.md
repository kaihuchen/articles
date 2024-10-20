<banner class="page-header" role="banner">
  <img src="../assets/images/schizoBot.png" alt="Banner Image" style="">
</banner>

# How to Create a GenAI Go-To-Market Playbook Using a Multi-Role Chatbot

*Published 2024.10.16*

There are many ways to create a large language model (LLM)-based system where multiple agents collaborate to accomplish a task. Typically, this involves using multiple LLM chatbots. However, in this article, we will explore how to achieve this with only a single LLM chatbot by authoring a Generative AI (GenAI) Go-To-Market (GTM) Playbook as a use case.

The core concept of this approach is to define multiple roles or personalities within a single chatbot, with each role assigned a specific perspective on the overall goal. These roles then work together, sometimes even in adversarial positions, under the guidance of a human user.

#### Why Use a GenAI GTM Playbook as a Test Case

We have chosen to create a GenAI GTM Playbook as our test case for this approach. A GTM Playbook is a document that outlines an actionable series of steps designed to help teams build their go-to-market strategy and plan, aligning all marketing and sales activities while also considering the needs of targeted customers.

A GenAI GTM Playbook serves as an excellent test for our multi-role approach because it is a complex document that must reconcile the perspectives of multiple stakeholders.

It is worth noting that if you ask a leading LLM chatbot to create a GenAI GTM Playbook, you might receive a document that is somewhat in the right direction but lacks depth and omits many vital details.

Using the multi-role chatbot approach, we can define multiple roles, each corresponding to a stakeholder in the playbook. This setup allows each role to critique a draft of the playbook from its specific perspective in multiple rounds, enabling a "playbook owner" role (named Bot-playbook-owner) to incorporate parts of the input at their discretion into the playbook.

#### Experimental Setup

1. **Model Selection**: We used OpenAI's **o1-preview** model (referred to as **o1** throughout) to simulate the process.

2. **Role Identification**: The o1 model has identified **46 distinct roles** relevant to the Go-To-Market (GTM) playbook. These roles encompassed perspectives from the **solution buyer** side (e.g., procurement), the **solution vendor** side (e.g., marketing and product leads), and external stakeholders (e.g., regulators or partners). Although this detailed breakdown may seem overly granular, it provides a comprehensive reference for a human author by covering a wide range of relevant viewpoints. 

   Each role's definition includes its role name and area of interest. For example:
   - **Role:** Bot-Vendor-CEO  
   - **Area of Interest:** Strategic vision and high-level direction of the GenAI solution, including approval of significant investments and partnerships. This role ensures that the GTM strategy aligns with the company’s long-term objectives. 

    [Complete list of roles initially created](roles.md)

3. **Domain Selection**: The **healthcare industry** was chosen as the focus of this experiment. However, the same approach could easily be applied to other fields such as finance, law, education, etc.

4. **Experimental Process**: The experiment involved multiple rounds of interaction between the simulated roles to refine the playbook. The workflow included:
   1. **Draft Creation:** A designated “playbook owner” role within the chatbot generated an initial version of the GTM playbook.
   2. **Role Critique:** Other roles reviewed and critiqued the draft, suggesting improvements or raising concerns.
   3. **Revision & Response:** The "palybook owner" role responded to each critique, either by updating the playbook or pushing back with a rationale. 
   4. **Human Intervention:** At any point, human author could introduce new roles or adjust existing ones to steer the playbook in a particular direction or address emerging challenges. Human user could also instigate interactions bewteen specific roles on a particular topic. Overall, this setup not only support fine-grained adjustments, but also make the entire process more transparent.

This "Multi-role Chatbot" approach enables the rapid creation of a practical GenAI GTM playbook draft, which can be incrementally improved by focusing on specific aspects to enhance it step by step.

## Sample Interaction 

Below is an example showcasing the interaction between **Bot-playbook-owner** and **Bot-vendor-marketing**, where **Bot-vendor-marketing** represents the interests of the marketing department of the solution vendor. The following excerpt is from version 3 of the playbook draft, which is still relatively skeletal:

  - **Digital Marketing**

    - **Platform Selection:**
      - Focus on LinkedIn, Doximity, and specialized forums like Medscape.
    - **Content Strategy:**
      - Regular blog posts on AI in healthcare, compliance tips, and success stories.
    - **SEO and SEM:**
      - Optimize for keywords like "AI healthcare solutions," "compliant AI tools," etc.

The human author (i.e., the User) can remedy this by issuing the following prompt to the chatbot:

  **User**: To Bot-vendor-marketing: please give your detailed input regarding the latest playbook draft
  **o1**(as Bot-vendor-marketing):
  > **Detailed Input Regarding the Latest Playbook Draft**
  >
  >  Dear Bot-playbook-owner,
  >
  >  Thank you for the comprehensive update to the Go-To-Market (GTM) playbook. The inclusion of detailed content and actionable insights significantly enhances its value. From a marketing perspective, I have reviewed the latest draft thoroughly and would like to provide my detailed input to further strengthen our strategy.
  >
  >  ### **1. Marketing Strategy (Section 6)**
  >
  >  #### **6.1 Marketing Channels**
  >
  >  **Digital Marketing**
  >
  >  - **Platform Expansion:**
      - While LinkedIn, Doximity, and Medscape are excellent platforms, consider expanding to include Twitter and professional groups on Facebook, where healthcare professionals actively engage in discussions.
      - Leverage healthcare-focused online communities such as Sermo and QuantiaMD for targeted outreach.
  >
  >  - **Content Strategy:**
      - In addition to regular blog posts, incorporate multimedia content like infographics, short videos, and podcasts to cater to different content consumption preferences.
      - Develop interactive content such as quizzes or calculators related to compliance readiness or AI maturity in healthcare.
  >
  >  - **SEO and SEM:**
      - Conduct comprehensive keyword research to identify long-tail keywords and questions that healthcare professionals are searching for.
      - Implement an SEO strategy that includes optimizing meta tags, improving site speed, and ensuring mobile responsiveness.
      - Allocate budget for Google Ads and LinkedIn Sponsored Content to increase visibility.
      **(many more text ommited)**

From here if satisfied then the human author can direct the *Bot-playbook-owner* role to incorporate all or part of the suggested text and regenerate the full playbook. Below is a sample interaction for this:

**User**: To Bot-playbook-owner: please proceed to incorporate all or part of the suggestion, and give me the full draft. If part of the suggestions are omitted or substantially changed, then please indicate your reason for doing so.
**o1**(as Bot-playbook-owner):
  > (Text of the playbook omitted. See playbook_v4 below for full text.)
  > **Notes on Suggestions Not Fully Incorporated or Adjusted:**
  >
  >- **Public Relations (PR) Agency Engagement:**
    - While engaging a PR agency specializing in healthcare technology is a valuable suggestion, we have decided to first leverage our in-house PR capabilities to manage media relations and press releases. This approach allows us to maintain close control over our messaging and manage costs effectively. We will reassess the need for an external PR agency after evaluating the results of our initial efforts.
  >  
  >- **Employee Advocacy:**
    - We agree that employee advocacy can expand our reach. However, to ensure compliance with healthcare regulations and company policies, we will develop clear guidelines and provide training before encouraging employees to share company content. This will be implemented in a controlled manner to mitigate any potential risks.
  >

Note that Bot-playbook-owner has chosen to reject some of the suggestions from Bot-vendor-marketing.

## Sample GTM Playbook drafts

Below is a list of several iterations of the Playbook:

1. [Playbook draft #1](playbook_v1.md): this is the first draft created by Bot-playbook-owner, without any input from other bots.
2. [Playbook draft #4](playbook_v4.md): this is the result of Bot-playbook-owner accepting some of the suggestions from Bot-vendor-marketing.

Please note that the drafts provided above are works in progress for your reference only, and there is still much work to be done before the playbook can be considered nearly complete.

## Sample prompts

- The following is the prompt used for enumerating the roles relevant to this GenAI GTM Playbook: 
  > when creating a GTM playbook for GenAI solutions, many parties (both on the solution vendor side and the solution buyer side) have a stake in defining or following the playbook. List all parties that have such a stake, including their area of interests in detail, also assign each party a unique ID in the form of "Bot-vendor-marketing" etc. Note that one party in particular, which is the writer of this playbook, shall be named as "Bot-playbook-owner".  
- The following is the prompt used for defining the roles and their respective responsibilities. Also define their unique names for ease of reference:
  > For the purpose of creating a better playbook by reviewing and debating relevant issues from the perspective of each party, I want you to define 46 "personalities," where each represents strictly the interests of a party in the list that you gave above. Each "personality" will be referenced by its ID, such as "Bot-playbook-owner", and when called upon should proceed to respond to my command based on its assigned personality. 
- The following is the prompt for instructing the playbook owner role, Bot-playbook-owner, to create the first draft of the playbook.
  > Bot-playbook-owner, please proceed to create the first draft of the said playbook in as much details as you could, taking into consideration of the interests of each party.

### Summary

What are the strengths and weaknesses of this approach, and how can we make it better? Here is what the o1 model thinks (which is quite to the point):

  > **User**: you are an expert in GenAI technologies. In your opinion is the approach mentioned in the given article novel and effective?
  > **o1**: The approach described in the article—using a "schizophrenic chatbot" where multiple roles simulate stakeholders to collaboratively create a GenAI Go-To-Market (GTM) Playbook—is both **novel** and **partially effective**. However, it has limitations and can be further optimized by aligning with best practices in multi-agent and collaborative LLM systems.
  >
  > ### Novelty of the Approach
  > 1. **Role-Based Simulation for Complex Document Creation**:
  >     - Assigning multiple stakeholder roles to a single chatbot to refine a document through iterative back-and-forth interactions is an innovative take. This approach mimics real-world collaborative processes but within an LLM-driven framework. It draws from **multi-agent systems** (MAS) research, where agents handle specialized tasks to generate better results collaboratively.
  >     - While role-specific agent-based frameworks are becoming popular in simulation and planning tasks, applying them to generate a comprehensive GTM playbook is a fresh use case.
  >
  > 2. **Integration of Conflicting Perspectives**:
  >     - This method directly tackles the challenge of **conflicting interests** between stakeholders (e.g., vendors, buyers, regulators). By simulating this interaction, the LLM attempts to uncover gaps that might not emerge through a single-agent generative process. This makes the approach distinct compared to typical LLM-generated outputs, which tend to be overly generic and shallow.
  >
  > 3. **Human-Augmented Workflow**:
  > - The ability to inject new roles and perspectives mid-process adds a layer of **dynamism**. This aligns with trends in agentic systems where user interventions can direct or correct outcomes in complex workflows.
>
> ### Effectiveness and Limitations
> 1. **Strengths**:
  >     - **Improved Drafting Quality**: The iterative feedback mechanism among roles ensures that the document becomes more refined over time.
  >     - **Time Savings**: Generating initial drafts with LLMs accelerates document creation, especially for **highly structured** content like GTM playbooks.
  >     - **Simulated Collaboration**: Simulating complex stakeholder interactions mimics real-world scenarios, providing a better first draft compared to single-agent LLM outputs.
  >
  > 2. **Challenges and Limitations**:
  >    - **Efficiency Issues**: The iterative approach involving multiple roles can become cumbersome. Each role might repeatedly engage in redundant exchanges, slowing down the generation process.
  >    - **Lack of Contextual Depth**: While the roles provide perspectives, the approach may not entirely capture the nuance required for GTM strategies in specialized industries without external data sources or tools (e.g., financial forecasts or compliance regulations).
  >    - **Risk of Hallucination**: Although having multiple roles reduces the likelihood of hallucination, the underlying LLM still carries the risk of generating inaccurate content if not properly monitored or validated.
>
> ### Conclusion
> In summary, the proposed approach is **novel** and demonstrates potential effectiveness for generating complex documents. It aligns with current trends in **multi-agent orchestration** and **collaborative workflows** using LLMs. However, its effectiveness would improve with further optimizations, such as introducing **external tools**, **dynamic role prioritization**, and **real-time human oversight**. 
>
>While this approach isn't a replacement for professional authors or consultants, it offers a valuable framework for rapidly developing complex documents, especially in domains where multiple viewpoints and iterative refinement are essential.




<!-- <details>
  <summary>Complete list of roles initially created</summary>
</details> -->

<!-- <banner class="page-header" role="banner">
  <img src="../assets/images/q3.webp" alt="Banner Image">
</banner> -->

