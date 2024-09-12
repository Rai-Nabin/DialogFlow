# Building Advanced Chatbots and Voice bots using Dialogflow CX
Resources:
- Video Tutorial: [link](https://www.youtube.com/watch?v=k2lma22109w&list=PLG9FQRMgm_JKTyvzTj7Z9jizHjwT9g-k8&index=3)
- Google Codelab: [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#6)

---

* **Conditional Responses in Dialogflow CX:**  Dialogflow CX allows you to create dynamic, branching conversations where the chatbot's responses adapt based on specific conditions. This is a powerful feature that was not easily achievable in Dialogflow Essentials.
* **The Need for Control:** Businesses that rely on chatbots for customer interactions often require more control over the conversation flow. They might want to personalize responses, offer different paths depending on user preferences, or handle specific scenarios differently. 
* **Conditional Templating:**  Dialogflow CX allows you to include if/else logic within your response templates. This means you can create different responses based on values of parameters, conditions, or other factors.
* **Enterprise Benefits:**  This feature is especially valuable for enterprises where dedicated teams work on creating chatbot workflows and conversations. It empowers them to build more sophisticated and tailored chatbots.

**Example Use Cases:**

* **Personalized Greetings:**  You could create a greeting that says "Good morning" if the current hour is before noon and "Good afternoon" otherwise.
* **Order-Specific Responses:** You could display different information depending on the merchandise type. For example, if a user orders a T-shirt, you could ask for their shipping address, while for digital music, you could skip that step.
* **Dynamic Product Information:**  You could provide different product details based on the selected item. For example, you could show a description of a T-shirt or a tracklist for an album.

**How it Works:**

* **If/Else Logic:**  You'll be able to use if/else statements within your response templates, allowing you to create different responses based on conditions.  
* **Parameters and Values:**  The conditions can be based on the values of parameters collected during the conversation.
* **Contextual Responses:**  The chatbot's responses will be more tailored and relevant to the user's context and selections.

**Benefits:**

* **More Dynamic Conversations:** Chatbots become more engaging and provide a more personalized user experience. 
* **Flexibility and Control:**  You gain more control over the conversation flow and can create branching paths to handle different scenarios.
* **Increased Efficiency:** You can avoid repeating the same information or providing unnecessary details based on the user's choices.

---

**1.  Setting Up the "My Order" Flow**

* **Purpose:** This flow specifically handles user interactions related to their orders, such as checking the status or canceling an order.
* **Dedicated Flow:**  Creating a separate flow for "My Order" helps organize the conversation and makes it easier to manage different parts of the chatbot. 
* **Intents and Transitions:**  Intents are defined for specific user requests within this flow, such as "My Order," "My Order Status," "Cancel," and "Go Back." Each intent is then linked to a specific page, directing the conversation flow.
* **Pages:**  Pages within the "My Order" flow are created to handle different steps in the order management process.  For example, the "Order" page will likely ask for the order number, the "Status" page will display the order status, and the "Cancellation" page will confirm the cancellation.

**2.  "Order Number" Parameter:  The Foundation for Order Management**

* **Purpose:** The "Order Number" parameter is a crucial element that stores the user's unique order number, allowing the chatbot to retrieve order details and process their request.
* **Required Parameter:** The "Order Number" is marked as required, meaning the chatbot won't proceed to the next step until the user provides a valid order number. This ensures the chatbot has the necessary information to fulfill the user's request.
* **Initial Prompt:**  An initial prompt is set up to ask the user for their order number when they enter the "My Order" flow. 
* **Validation:** The chatbot may include logic to validate the format of the order number, ensuring it matches the expected pattern.

**3.  Conditional Responses: Tailoring the User Experience**

* **Purpose:** Conditional responses are used within the "My Order" flow to deliver different messages based on the user's action and the order information.  
* **Examples:**
    * **Order Status:** If the order is "Shipped," the chatbot might respond with a message like, "Your order has been shipped and is expected to arrive within two weeks."
    * **Order Cancellation:**  If the order is successfully canceled, the chatbot might confirm with a message like, "Your order has been canceled. You will receive a confirmation email."
* **Dynamic Content:** Conditional responses allow you to create more dynamic and personalized messages, making the user experience more engaging.

**4.  Event Handlers:  Managing Unexpected Scenarios**

* **No Input:** The chatbot will handle situations where the user doesn't provide an order number or pauses for a longer time. A re-prompting message will be delivered, reminding the user to enter their order number.
* **No Match:**  If the user provides an invalid order number format, the chatbot will provide a message explaining the correct format, ensuring the user can provide a valid order number.

**5.  Resetting Parameters:  A Clean Slate for the Next Interaction**

* **Purpose:**  When the user declines to confirm an order, it's important to reset all the parameters to their default values.  This ensures that the chatbot starts fresh for the next interaction, preventing any confusion or errors due to previously selected values.
* **Parameter Presets:**  The chatbot can set parameter presets to automatically assign a value to a parameter when a specific page becomes active. For example, when the user cancels an order, a "restart" parameter could be set to "true" to indicate that a new session is starting.

**6.  Welcome Message:  Recognizing Returning Users**

* **Purpose:**  If a user has previously interacted with the chatbot, a personalized welcome message can be displayed when they return. This creates a more engaging experience by recognizing their previous interactions.
* **Session Parameter:**  The "restart" parameter is used to track if the user has interacted with the bot before. A condition is set up that checks the "restart" parameter. If it's true, the welcome message will change to something like, "Welcome back!"

**7.  Goodbye Message: Ending the Conversation**

* **Purpose:**  A custom goodbye message is added to the default start flow to provide a polite and informative ending to the conversation when the user chooses to end the session. This adds a final touch to the user experience.

---

**1. Negative Intents:  Training the Bot to Understand What It *Doesn't* Mean**

* **Purpose:**  Negative intents help train your chatbot to recognize phrases that should *not* trigger a specific intent. This ensures that the chatbot doesn't misinterpret user input and stays on the correct conversational path.
* **Examples:**
    * **"I don't like Alice Googler":**  You might have an intent for "Order Alice Googler Merchandise," but you don't want this intent to trigger when a user says they don't like the artist. 
    * **"I want to block my card":**  You might have an intent to close an account, but you don't want it to trigger if the user wants to block their card.
* **Training Phrases:**  You create negative intents by adding training phrases that represent the kinds of phrases you *don't* want to trigger the intent. 
* **No Match Event:**  When a user input matches a negative intent, it will usually trigger a "no match" event handler, allowing you to provide a more appropriate response.

**2. Default Fallback Messages: Handling Unforeseen Scenarios**

* **Purpose:**  Default fallback messages are used to provide responses when the chatbot cannot understand the user's input or if no input is provided. 
* **"No Input" vs. "No Match":**
    * **"No Input":** The user doesn't provide any response.
    * **"No Match":** The user provides input, but it doesn't match any defined intents.
* **Specificity:**  It's best practice to create specific fallback messages for each event. For example, if no input is provided, you could ask the user to repeat their request. If there's no match, you could suggest ways to rephrase their request.

**3.  "Order Process" Flow: Capturing User Details**

* **Purpose:** This flow handles the steps involved in collecting user information to complete an order, such as name, address, and potentially payment details. 
* **Parameters:**  Parameters are used to store the user's information as they are provided.
* **Conditional Logic:**  Conditional logic can be used to tailor responses based on the collected information. For example, if the user has already provided their address, the chatbot might skip asking for it again.

**4.  Key Considerations:**

* **User Privacy:**  When handling personal information like addresses, it's essential to follow data privacy regulations and secure user data.
* **Integration with Backend Systems:**  To process orders, you'll need to integrate the chatbot with your backend systems, such as an order management system or a payment gateway.

---

**1. Setting Up the "Order Process" Flow**

* **Purpose:**  This flow handles the process of capturing user details necessary to complete an order. It's the final stage of the chatbot's interaction with the user, leading to order confirmation and (in a real-world scenario) payment processing.
* **Intents and Transitions:** The flow uses intents to recognize user actions and transitions to move between pages based on those actions:
    * **"Confirm Proceed Order":**  This intent triggers the transition to the "Shipping Details" page, where the user's information is collected.
    * **"Decline Proceed Order":** This intent triggers a transition back to the "Welcome" page, resetting all the parameters and clearing the shopping cart.
* **Pages:** Each page within the flow handles a specific step:
    * **"Shipping Details":**  Captures the user's name, address, and email address. 
    * **"Confirmation":**  Provides a summary of the order and allows the user to confirm. 

**2.  "Shipping Details" Page:**  Collecting User Information

* **Parameters:**  Required parameters are defined to capture the user's details:
    * **First Name:**  A system entity (pre-defined by Dialogflow) is used to capture the user's first name.
    * **Last Name:**  A system entity is used to capture the user's last name.
    * **Address, Postal Code, City, Country:** System entities are used to gather the user's address information.
    * **Email Address:** A system entity is used to capture the user's email address.
* **Initial Prompts:**  Each parameter has an initial prompt to guide the user and request the specific information.
* **Event Handlers:**  "No Input" and "No Match" event handlers are implemented to handle situations where the user doesn't provide input or provides an invalid format. 
* **Conditional Routing:**  Once all the parameters have been filled, the flow transitions to the "Confirmation" page. 

**3. "Confirmation" Page:  Summarizing and Confirming the Order**

* **Conditional Responses:**  The "Confirmation" page utilizes conditional responses to provide different messages depending on the order details.
    * **Digital Album:**  The chatbot informs the user that no shipping costs are required for digital albums and that a link will be sent to their email address.
    * **Physical Items (T-Shirt, CD, Tour Movie):** The chatbot calculates the total cost (including shipping) and displays the user's shipping address.
* **Payment Integration:** The tutorial uses a placeholder message suggesting Google Pay integration. In a real-world scenario, you'd integrate with a payment gateway API to process the transaction.
* **User Confirmation:** The user is prompted to confirm the order by explicitly saying "I Confirm." 

**4.  Best Practices and Considerations**

* **User Experience:**  The "Order Process" flow prioritizes a clear and user-friendly experience, guiding the user with helpful prompts, informative messages, and clear next steps.
* **Voice-First Design:** The tutorial emphasizes voice-first design by ensuring that responses and prompts are suitable for conversational interactions.
* **Data Privacy:** The tutorial reminds developers to follow data privacy regulations when collecting and storing user information.
* **Integration with Backend Systems:**  For real-world implementation, you'll need to integrate with backend systems like an order management system, payment gateway, and potentially a shipping provider.

**5.  Key Takeaways**

* **Flow Structure:** Creating a well-structured flow with specific intents and pages makes the conversation clear and manageable. 
* **Parameters:**  Parameters are essential for capturing user information and providing context to the conversation. 
* **Conditional Responses:** Conditional responses are critical for providing dynamic and personalized experiences, tailoring responses to user choices.
* **Event Handlers:**  Event handlers handle unexpected situations, ensuring a smooth user experience even when things don't go as expected.
* **Real-World Integration:** The tutorial highlights the importance of integrating with real-world systems to complete orders and handle payments.

---


