# Building Advanced Chatbots and Voice bots using Dialogflow CX
Resources:
- Video Tutorial: [link](https://www.youtube.com/watch?v=bpzSQTZ9MzI&list=PLG9FQRMgm_JKTyvzTj7Z9jizHjwT9g-k8)
- Google Codelab: [link](https://codelabs.developers.google.com/codelabs/dialogflow-cx-retail-agent#0)

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

