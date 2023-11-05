- {{renderer :wordcount_}}
	- this is a conversation with llama2 but it has been given a personality
		- ```
		  
		  ```
	- this is nothing new as the same can be done with chat-gpt by giving the prompt information so as to instruct the LLM to respond in a given way however this differs significantly in that the llama model has itself been augmented so as to take on this pre-prompt for every session, thus sustaining a configured state between sessions. This is something that chat-gpt in its current form cannot do, rather, state or variable input needs to be managed in pre-promts and in turn held by the client, where each prompt starts out as big as it needs to be in order to do this and will always have that initial payload there after with subsequent connected sessions.
	- I understand that llama2 and other models can be augmented, trained if you would, but I came across a tool on Github that wraps this for you into an application that calls itself [ollama]