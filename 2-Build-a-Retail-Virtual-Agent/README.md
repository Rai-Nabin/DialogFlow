# Building Advanced Chatbots and Voice bots using Dialogflow CX
Resources:
- Video Tutorial: [link](https://www.youtube.com/watch?v=PGOWuHhi0Mg&list=PLG9FQRMgm_JKTyvzTj7Z9jizHjwT9g-k8&index=2)
- Google Codelab: [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#5)
---

* **State Machines:** A state machine is a model where a system moves through different states. Imagine a vending machine: it has states like "selecting candy," "inserting coins," and "dispensing candy."
* **Pages in Dialogflow CX:** Pages in Dialogflow CX represent different states in a conversation. When a user interacts with the chatbot, the conversation transitions from page to page, following a defined path.
* **Active Page & Flow:** Only one page is active at a time, and this active page belongs to an active flow. Multiple pages can be defined for a single flow, forming a complete conversation.
* **Default Start Page:** Every flow has a default start page, which becomes active when the flow is initiated.
* **Transitioning Through Pages:** Once the conversation starts, it moves from the start page to other pages based on user input and the predefined flow logic.
---

- **Pages as Movie Scenes:** Pages are like scenes in a movie, with conversations and actions taking place within each page.
- **Flows as Film Locations:** Flows are analogous to locations in a movie, with multiple pages (scenes) within a single flow.
- **Fulfillment:** Pages contain fulfillments, which can be static dialogues (hardcoded text responses) or dynamic webhooks (responses fetched from a database or other API).
- **Parameters:** Pages can hold parameters, which are variables that store information like a t-shirt size.
- **State Handlers & Routes:** State handlers control the flow of the conversation by using routes to transition between pages.
- **Route Types:**
    
    - **Intent Routes:** Triggered when a user's input matches a specific intent.
    - **Condition Routes:** Triggered based on a specific condition (e.g., only proceed if a t-shirt size is provided).
    - **Event Handlers:** Triggered by events like a fallback (no matching intent), no input, or webhook failure.
- **Multiple Webhooks in CX:** Dialogflow CX allows you to have different webhook URLs for different pages and flows, making it easier to manage backend integration compared to Dialogflow Essentials.
- **Route Groups:** Group related pages together to simplify management and reuse intent routes.

---

* **Connecting Flows:**  The video shows how to connect the default start flow to other flows using intent routes. Each intent route is linked to a specific flow, directing the conversation based on the user's intent. 
* **Visualization:** Dialogflow CX offers a visual representation of the connected flows, showing intent routes (blue lines), condition routes (orange lines), and event handlers (green lines).
* **Flow as a Subject:** Flows should represent a specific topic or task. Avoid creating overly small or numerous flows, as this can make the conversation flow complex and difficult to manage. 
* **Ending Flows:** It's crucial to end flows properly using either:
    * **End Session:**  Completely closes the chat session, similar to hanging up a phone call.
    * **End Flow:**  Closes the current flow and returns to the last active flow. This is essential for nested conversations, where you might want to jump back to a previous flow.

**Important Considerations:**

* **Default Behavior:** Dialogflow CX tries to stay within a conversation flow until it reaches the end. If you jump to a different flow and don't end it properly, you might create nested conversations, which can lead to errors.
* **Flow Design:** When designing conversational flows, think about how to break down the conversation into logical, manageable flows. 
* **Documentation:** Refer to the Dialogflow CX documentation for detailed information about flows, intents, and best practices.

---

* **Script First:** First create a flowchart to visualize the page flow, and finally configuring the pages in the Dialogflow CX tool.
* **Complex Conversation Flow:**  The example conversation involves multiple pages, intents, and flows, demonstrating the power and flexibility of Dialogflow CX.
* **Reusable Pages:**  Pages can be reused across different flows, allowing for more efficient development. For example, the "price" page can be accessed from various points in the conversation.
* **Dialogflow CX vs. Essentials:** CX is better suited for complex chatbots with multiple flows and intents, while Essentials is more appropriate for simpler, linear conversations.
* **CX Benefits:**  Dialogflow CX offers a visual flow builder, multiple webhook URLs, and a more user-friendly interface, making it easier for developers and bot designers to work together.
* **Cost Considerations:** Dialogflow CX has a higher cost than Essentials, but it offers more features and capabilities, making it a good investment for complex chatbot projects. 

**Key Differences:**

* **Flow Building:** Dialogflow CX offers a visual flow builder, while Essentials requires developers to write code for flow logic.
* **Webhooks:** CX allows for multiple webhooks per flow, while Essentials uses a single webhook for the entire bot.
* **Complexity:** CX is designed for more complex chatbots, while Essentials is better for simpler interactions.

---

1. **Creating Pages:**  Pages are created within the "Catalog" flow, each representing a distinct part of the conversation. Examples include "Artist Overview" and "Product Overview" pages. 
2. **Connecting Pages with Intents:**  Intent routes are set up to link intents to specific pages, directing the conversation based on user input. 
3. **Testing in Simulator:**  The flow is tested in the simulator to ensure that the chatbot responds correctly to user inputs.
4. **Rich Content & Custom Payloads:** Custom payloads are used for rich content, allowing the chatbot to display information in a visually appealing way, such as suggestion chips. 
5. **Follow-up Questions:**  The importance of follow-up questions to guide the conversation is highlighted. For example, after displaying the list of signed artists, the chatbot should ask "Which artist would you like to order merchandise from?"

**Key Points:**

* **Visualizing Conversation Flow:** It's essential to visualize the conversation flow using a flowchart or similar tool to understand the connections between pages and the overall conversational path.
* **Testing:**  Thorough testing is needed to ensure the chatbot handles different user inputs correctly and smoothly transitions between pages.
* **Default Start Flow:**  The default start flow is used to route users to other flows based on their initial intent.
---

**1. Page Parameters: Capturing User Information**

* **Purpose:** Page parameters are like variables that store information provided by the user during a conversation. They are essential for gathering data necessary to fulfill the user's request or guide the conversation. 
* **Examples:**
    * **Artist Name:**  Used to identify the artist whose merchandise the user is interested in.
    * **Merchandise Type:**  Determines whether the user wants a T-shirt, music, or a tour movie.
    * **Shirt Size:** Needed if the user is ordering a T-shirt.
* **Required Parameters:**  Some parameters are marked as required, meaning that the chatbot won't proceed until it has gathered the necessary information. This ensures that crucial data is collected before moving to the next step.
* **Context:** Page parameters provide context to the conversation. They help the chatbot understand the user's intent and provide personalized responses.

**2. Response Messages: Providing Feedback**

* **Purpose:**  Response messages provide feedback to the user, guiding them through the conversation. They can be triggered by different events, such as:
    * **Page Activation:** The initial message displayed when a page becomes active.
    * **No Input:**  The user didn't provide any input after being prompted.
    * **No Match:** The user's input didn't match any defined intents. 
* **Key Considerations:**
    * **Clarity:**  Response messages should be clear, concise, and easy to understand. 
    * **Helpfulness:** They should provide guidance, re-prompt the user, or clarify the next steps in the conversation.
    * **Specificity:**  The messages should be specific to the context of the conversation.

**3. Event Handlers: Managing Unexpected Situations**

* **Purpose:** Event handlers are triggered by specific events, allowing the chatbot to handle unexpected situations or deviations in the conversation flow. 
* **Examples:**
    * **No Input:** The user might take time to respond or doesn't provide an answer. 
    * **No Match:** The user's input doesn't match any of the defined intents.
* **Key Roles:**
    * **Error Handling:**  Event handlers provide a mechanism to recover from unexpected user input.
    * **Re-prompting:** They can re-prompt the user for information or guide them to the correct path.
    * **Contextual Feedback:**  Event handlers should provide relevant and helpful messages to the user.

**4. Custom Payloads: Enhancing the User Experience**

* **Purpose:** Custom payloads enable the chatbot to display rich content, such as suggestion chips, images, or cards, making the conversation more interactive and visually appealing.
* **Key Benefits:**
    * **Improved User Engagement:**  Rich content enhances the user experience by making the conversation more engaging and visually interesting.
    * **Enhanced Information Display:**  Custom payloads allow for more informative and visually appealing presentations of data.
    * **Platform Flexibility:** Custom payloads can be tailored to different platforms, ensuring consistency across various integration channels. 

**5. Flow Visualization: Keeping Track of the Conversation**

* **Importance:**  Visualizing the conversation flow through a flowchart or similar tool is essential for:
    * **Understanding Complex Flows:**  Visual aids help to understand how different pages are connected, especially in complex conversations.
    * **Identifying Potential Issues:**  Flowcharts can reveal potential problems in the conversation logic.
    * **Collaboration:** They facilitate collaboration among developers and designers, ensuring everyone is on the same page.

 ---

**1. Conditional Routes: The Foundation of Dynamic Conversations**

* **Purpose:** Conditional routes are a crucial feature in Dialogflow CX that allows your chatbot to dynamically branch the conversation based on specific conditions.  Instead of following a linear path, the chatbot can make decisions and navigate to different pages or flows based on what the user has said or what data has been collected. 
* **Think of it like a Decision Tree:** Imagine a tree where each branch represents a different path based on a choice.  Conditional routes work like this in Dialogflow CX, letting you build branching conversations based on user input and gathered information.

**2. Key Conditions That Drive Decision-Making**

* **Parameter Values:** You can create conditions that check if a specific parameter has a particular value.  For example, if the "Artist" parameter has a value of "Alice Googler," then the chatbot could transition to a page that displays Alice Googler's merchandise. 
* **Parameter Presence:** You can make sure that a required parameter has been provided by the user before transitioning to the next page. For instance, if the "Shirt Size" parameter is required, the conversation might branch to ask for the size if it's not yet provided.
* **Form Completion:** You can ensure that all the necessary parameters have been filled out before proceeding to the next stage of the conversation. For instance, if the "Artist" and "Merchandise Item" parameters are needed, the conversation might loop back and ask for those values if they are missing. 

**3. The Power of "Or" and "And" Rules**

* **"Or" Rules:**  These are used when any one of the specified conditions needs to be met for the transition to happen. For example, if the user has provided either "Artist Name" or "Merchandise Type," the conversation could proceed.
* **"And" Rules:** These are used when all of the specified conditions must be met. For example, if both "Artist Name" and "Merchandise Item" are present, the chatbot could transition to the "Confirmation" page.

**4. Handling "Not Met" Conditions**

* **Best Practices:**  It's essential to consider what happens when the conditions you set are not met.  For a smooth user experience, create paths in your flow that handle these scenarios, such as:
    * **Re-prompting:** If a parameter is missing, the chatbot could politely ask for the missing information.
    * **Providing Guidance:** If a user's input doesn't match any intents, you could provide guidance on how to phrase their request correctly.
    * **Preventing Errors:**  You can use conditions to ensure that the user's selections are valid and prevent the chatbot from making mistakes. 

**5. Visualizing the Flow:  A Must-Have for Complex Conversations**

* **Importance:**  When building complex chatbot flows with conditional routes,  visualizing the conversation path is crucial.  
* **Tools:**  
    * **Dialogflow CX Flow Editor:**  Dialogflow CX has a built-in visual flow editor that allows you to see the connection between pages, intent routes, and conditional routes.
    * **Flowcharts:** Creating flowcharts is a great way to visualize your conversation logic, making it easier to spot any potential problems or missing conditions. 

**6. The Power of Parameter Presets**

* **Purpose:** Parameter presets allow you to automatically set a value for a parameter when a specific page becomes active. This is useful for:
    * **Default Values:**  Setting a default value for a parameter if the user doesn't provide it.
    * **Pre-filling Information:**  If you have certain information that is always true, you can set it as a parameter preset to save the user time and effort. 

**Example Scenarios:**

* **Ordering a T-Shirt:**
    * **Condition 1:**  If the "Artist Name" and "Shirt Size" parameters are present, transition to the "Confirmation" page.
    * **Condition 2:** If only the "Artist Name" is present, re-prompt the user for the "Shirt Size" and stay on the current page.
    * **Condition 3:**  If the "Artist Name" and "Shirt Size" are missing, transition back to the "Artist Overview" page and re-prompt the user for both parameters.

* **Asking about Music:**
    * **Condition 1:**  If the "Artist Name" and "Merchandise Type" are both present and the "Merchandise Type" is "Music," transition to a page that asks about the album. 
    * **Condition 2:**  If the "Artist Name" is present but the "Merchandise Type" is missing, transition to a page that asks the user what they want to order.






