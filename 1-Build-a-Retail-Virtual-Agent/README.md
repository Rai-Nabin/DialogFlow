# Building Advanced Chatbots and Voice bots using Dialogflow CX
Resources:
- Video Tutorial: [link](https://www.youtube.com/watch?v=bpzSQTZ9MzI&list=PLG9FQRMgm_JKTyvzTj7Z9jizHjwT9g-k8)
- Google Codelab: [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#0)

----

**What is Dialogflow CX?**

* Dialogflow CX is a conversational AI platform by Google Cloud for creating sophisticated virtual agents.
* It's ideal for building chatbots and voice bots designed for complex conversational flows, like those in contact centers.

**Dialogflow CX vs. Dialogflow ES (Essentials):**

* **Complexity:** Dialogflow CX excels in handling conversations with:
    * Many turns and back-and-forth exchanges.
    * The need to remember context deeply throughout the interaction.
    * Complex user journeys with multiple potential paths.
* **Contact Center Use Case:** It's well-suited for customer service scenarios where conversations tend to be longer and more intricate.
* **Framework and Code:** While you can build complex bots with Dialogflow ES, it often requires significant custom coding to manage the complexity. Dialogflow CX provides built-in features to handle this, reducing the need for external frameworks.

**Key Advantages of Dialogflow CX:**

* **Simplified Complex Conversation Design:** Makes it easier to build and manage bots that can handle intricate dialogs.
* **Powerful Context Management:**  Effectively keeps track of conversation history and user input for more natural interactions.
* **Reduced Development Effort:** Provides built-in tools and features that minimize the need for custom code. 
----
Codelab: [Demo](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#0)

**Introducing G-Records**

* The speakers are discussing building a retail chatbot for a fictional record label called "G-Records."
* The name is a play on "Google Records," and the idea is that the label signs bands with Google-themed names, like "Alice Googler," "G’s N’ Roses," "The Goo Fighters," and "The Google Dolls."
* This chatbot will allow users to:
    * Order band merchandise (t-shirts, CDs, tour movies)
    * Inquire about available bands and merchandise 

**Dialogflow CX Introduction & Benefits**

* Key benefits of Dialogflow CX are highlighted:
    * **Free trial with $600 credit:** Encourages experimentation and learning.
    * **Visual flow design:**  Allows for mapping out and controlling the conversational flow.
    * **Reusable components:**  Promotes efficiency by reusing common dialogue elements (like a login flow or shopping cart).
    * **Natural Language Understanding (NLU):** Powered by BERT, enabling the bot to understand and respond to varied user inputs.

**Dialogflow CX Concepts**

* Essential Dialogflow CX concepts are introduced, which will be used to build the chatbot:
    * **Flows:**  Represent distinct conversational paths (e.g., ordering merchandise, browsing artists).
    * **Pages:**  Individual steps within a flow.
    * **State Handlers:** Manage the transitions between pages based on user input.
    * **Parameters:**  Store information gathered during the conversation (like t-shirt size).
    * **Conditional Routes:**  Enable if/else logic to guide the conversation based on parameters.
    * **Fallbacks:** Handle unexpected user input.

**G-Records Chatbot Demo**

* The working G-Records chatbot is demonstrated:
    * It has a complex conversational flow, visualized as a tree with many branches. 
    * The demo shows how the chatbot interacts with a user through a web-based chat interface.
    * It successfully:
        * Greets the user and explains the purpose of G-Records.
        * Provides information about signed artists.
        * Guides the user through a merchandise purchase flow (selecting an artist, item, size, confirming the order).
---
Codelab: [Environment Setup](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#1)

1. **Setting up the Google Cloud Project:**
    * The first step involves creating a new project in the Google Cloud console. 
    * A billing account is required even for the free trial, to prevent misuse.
    * The project acts as a container for all resources related to the chatbot. 
    * The tutorial uses a sample project named "g records video".

2. **Enabling Dialogflow CX API:**
    * To use Dialogflow CX, its API needs to be enabled for the project. 
    * This can be done by searching for “dialogflow API” within the project.

3. **Navigating to Dialogflow CX Console:**
    * Once the API is enabled, the user is guided to the Dialogflow CX console.
    * This is where the chatbot will be designed and configured.

4. **Creating a New Agent:**
    * An "agent" represents the chatbot within Dialogflow CX.
    * A unique name ("g records video" in this case) is assigned to the agent.
    * The geographic location ("us-central-1" in this case) of the agent is crucial, as it determines the availability of features and language models. The tutorial emphasizes sticking to this region for consistency.
    * This location, once selected, cannot be changed later. 

5. **Understanding the Difference from Dialogflow ES:**
    * Unlike Dialogflow ES which allows only one agent per project, Dialogflow CX allows multiple agents within a single project. 
    * Each agent can be designed for different purposes or regions.

6. **Exporting and Importing Agents:**
    * Dialogflow CX allows exporting agents as blobs (binary large objects), unlike Dialogflow ES which uses JSON files. 
    * The blob format is not directly editable due to its complex representation of the chatbot's graphical flow. 

7. **Introduction to Flows:**
    * The concept of "flows" is introduced. 
    * These represent reusable conversational paths that can be shared or reused across different parts of the chatbot.

----
**Key Advantages of Flows:**

* **Compact & Organized:** Flows offer a structured and visual approach to designing chatbot conversations, making it easier to understand and manage even complex interactions.
* **Team Collaboration:**  CX allows multiple users to work on the same agent (chatbot) with specific roles and permissions, fostering better teamwork and preventing accidental modifications. 
* **Granular Control & Flexibility:** CX provides fine-grained control over individual flows, enabling adjustments to:
    * **Classification Threshold:**  This determines how closely user input needs to match an intent within a specific flow. Adjusting the threshold can improve accuracy by making intent matching more or less strict.
    * **NLU Type:**  Different flows can utilize different Natural Language Understanding (NLU) models (standard or advanced) based on the complexity of the conversation required.

**Workflow & Best Practices:**

* **Plan on Paper First:** Before diving into CX, it's crucial to first sketch out the entire conversation flow on paper. This helps visualize the user journey and identify the different conversation paths. 
* **Break Down into Reusable Components:** Deconstruct the overall chatbot interaction into smaller, reusable pieces ("flows"). This modular approach simplifies development and maintenance. For example, a retail chatbot could have separate flows for browsing the catalog, placing an order, checking order status, and handling customer care inquiries. 
* **Start Small & Test:** Don't try to build all flows at once. Start with a few essential ones, thoroughly test them, and gradually expand the chatbot's capabilities. 
* **Be Mindful of Limitations:** CX has limits on the number of flows, pages, and other elements. Refer to the official documentation for details and plan accordingly. 
---
Codelab: [Flows](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#2)

1. **Creating Flows:** The video demonstrates creating four flows: "Catalog," "Customer Care," "My Order," and "Order Process." These flows represent different conversational paths users might take within the chatbot. 
2. **Setting Up the Default Start Flow:** The focus then shifts to the "Default Start" flow. The initial "hello how can I help you" message is replaced with a more specific greeting that describes the capabilities of the chatbot (e.g., "I'm the virtual agent for G Records, specializing in bands, t-shirts, and orders. How can I help you?").
3. **Adding Suggestion Chips:** To guide users towards specific topics, suggestion chips are added using JSON code within a "custom payload." These chips provide users with options like "Catalog," "My Order," and "Customer Care."
4. **Understanding Rich Content and Platform Specificity:** The video explains that the suggestion chips are rendered differently depending on the platform (e.g., Dialogflow Messenger or a custom integration).  The chatbot's platform is able to interpret the JSON payload and display the chips accordingly.
5. **Importance of Intent Training:**  While the suggestion chips are added, the chatbot doesn't yet understand what to do when a user selects one of them. This functionality requires creating intents and training the AI to understand the phrases associated with each chip. This is a task that will be addressed in the next steps of the tutorial.

**Key Takeaways:**

* **Flow Structure:** Dialogflow CX allows you to create different flows to organize different conversational paths.
* **Clear Greeting:**  Provide a clear greeting that introduces the chatbot and its capabilities.
* **Suggestion Chips:** Use suggestion chips to guide users and make the conversation more efficient.
* **Rich Content:** Dialogflow supports various types of rich content, including chips, images, and cards.
* **Platform-Specific Rendering:** Rich content is rendered differently depending on the platform where the chatbot is integrated.
* **Importance of Intents:** Intents are crucial for training the chatbot to understand user input and respond appropriately. 
---
Codelab: [Entity](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#3)

**Entity Types: Keywords and Value Extraction**

* **Entity Types in Dialogflow:** Similar to entities in databases, they represent key objects or concepts that are essential for understanding user input.
* **Example: Ordering a T-shirt:** Imagine a user wanting to order a T-shirt. Entity types would include "artist," "shirt type" (long sleeve or regular), and "size."  
* **Database Analogy:** Think of entity types as the columns in your database that hold specific information about a record.
* **Data Extraction:**  During a conversation, the chatbot extracts values associated with these entity types (e.g., "Alice Googler" for "artist," "long sleeve" for "shirt type," and "medium" for "size").
* **Reusability:**  Entity types are reusable across different flows, allowing you to extract information consistently throughout the conversation.

**Custom vs. System Entity Types**

* **Custom Entity Types:**  These are created by the developer and represent unique concepts specific to the chatbot (e.g., "artist" or "album").
* **System Entity Types:**  Dialogflow already knows certain entities (e.g., "country," "currency," or "name"), so you don't need to create them. They are pre-built and ready to use.

**Creating Entities in Dialogflow CX**

The tutorial demonstrates creating entities like:

* **Artist:** Alice Googler, Google Dolls, G's n' Roses, Goo Fighters
* **Merch:** T-shirt, Long Sleeve
* **Album:**  Greatest Hits, Live
* **Shirt Size:** Small, Medium, Large, 3XL
* **Order Number:**  A regular expression is used to capture a specific pattern of alphanumeric characters.

**Key Takeaways:**

* **Entity Types are Essential:** They provide the framework for extracting relevant information from user input.
* **Entity Types are Reusable:** This saves time and effort when creating multiple flows.
* **Custom vs. System Entity Types:**  Choose the appropriate type based on your needs.
* **Regular Expressions for Patterns:**  Use them to capture specific formats like order numbers.

---
Codelab: [Intent](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#4)

**Key Points:**

* **Intents: Understanding User Intent:** Intents represent the user's purpose or goal in a conversational turn. In Dialogflow CX, they are simplified compared to Essentials, focusing solely on training phrases.
* **Training Phrases:** These are examples of user utterances that help the chatbot learn to recognize a specific intent. Multiple variations are needed for the chatbot to understand different ways to express the same intent.
* **Entity Recognition:** When creating training phrases, the chatbot can automatically recognize and tag entities that were previously defined. This helps to extract key information from user input.
* **Intent Naming Convention:** It's recommended to use a naming convention for intents, for example, prefixing them with "redirect," "confirm," "deny," or "okay" to clearly understand the purpose and action of each intent.
* **Connecting Intents to Flows:** While the video doesn't show it, the next step would be to connect these intents to specific pages or nodes within the flows. This determines which page or node the chatbot transitions to after recognizing a particular intent. 

**Intents in Action:**

The video uses the example of creating intents like "redirect artist overview," "confirm artist overview," "redirect price," etc. Each intent has multiple training phrases that cover different ways a user might ask for information related to that intent.

**Example:**

* **Intent:** `redirect.artist.overview`
* **Training Phrases:**
    * "Which bands are signed?"
    * "What artists are on the label?"
    * "From which bands can I buy merchandise?"

**Benefits of Intents:**

* **Natural Language Understanding:**  Intents allow the chatbot to understand user input and respond appropriately.
* **Flow Control:** They guide the conversation by determining the next page or node in the flow.
* **Structured Conversations:** They help to create more organized and predictable chatbot interactions.

**Overall:**

Intents are a crucial part of building conversational agents in Dialogflow CX. They enable the chatbot to understand user intent and seamlessly transition the conversation based on what the user is asking. By creating robust intents with multiple training phrases and connecting them to flows, you can build a chatbot that engages in natural and meaningful conversations.

---

| Core Concepts | Descriptions | References |
| ---- | ---- | :--: |
| Dialogflow CX | Dialogflow CX is designed for building complex conversational agents, suitable for scenarios like customer service in call centers, where the chatbot needs to handle multiple queries and maintain context over long conversations.<br>While Dialogflow ES (Essentials) is capable of handling simpler interactions primarily focused on intent matching and entity extraction, CX is built to manage more intricate conversational flows without requiring extensive coding.<br> |  |
| Agents | The core components that manage the conversations. Each agent represents a unique chatbot or voice bot. |  |
| Flows | They define a portion of the conversation and help break down the conversation into manageable sections. | [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#2) |
| Pages | Represent states in the conversation, helping in the progression from one part of the conversation to another. | [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#5) |
| Intents | User intentions that the bot recognizes and responds to. Each intent is linked to a particular page. | [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#4) |
| Entities | They extract and manage parameters or variables from user input, aiding in making the conversation dynamic. | [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#3) |
| Routes | They guide the conversation from one page or flow to another based on conditions or user inputs.<br> |  |
| Contexts | Help manage conversation state by storing temporary information about the conversation, such as the current topic or parameters. |  |
| Event Handlers | These trigger actions based on predefined events, such as user inputs or system-generated events, enhancing the bot’s responsiveness. |  |
| Fulfillment | Allows the bot to connect with external systems or services to retrieve or send data, enabling more personalized and functional interactions. |  |
| Versions and Environments | Facilitate version control and testing by allowing different versions of the agent to run simultaneously in different environments (e.g., production, staging).<br> |  |

**Building Multi-turn Conversations**

- Use **Flows** to manage complex, multi-turn conversations where the user might need to provide information over several steps.
- Employ **Branches** within Flows to manage different conversation paths based on user inputs or system responses.

