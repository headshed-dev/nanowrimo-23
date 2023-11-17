- {{renderer :wordcount_}}
	- this is where future shocks will be
		- https://www.amazon.co.uk/Complete-Future-Shocks-Vol-1/dp/1781085595/ref=asc_df_1781085595/?tag=googshopuk-21&linkCode=df0&hvadid=310961947917&hvpos=&hvnetw=g&hvrand=7330227033314110907&hvpone=&hvptwo=&hvqmt=&hvdev=c&hvdvcmdl=&hvlocint=&hvlocphy=9045538&hvtargid=pla-528818072137&psc=1&mcid=4ea26094c6263cafb419fb239536480d&th=1&psc=1
	- I've just had a conversation over a couple of days with several LLMs. I do this quite a lot now, going back and forth, finding and getting round the limitations of one or another
	- Pitching one against the other is not the excerise here, rather to find where the strengths of one are the weaknesses of another and vice versa so as to pick the right one in the right context
	- I had created a data objet in JSON that comprised of an object with a nested list of objects within it and wanted to use, I thought, json serializable in Dart to handle de-seriaizing it into a Dart object for me, which I promptly gave chat-GPT to do for me
	- it dutifully gave me back the typical code to do this in a 'models.dart' file, which subsequently I could use to regenerate the models.g.dart file with `flutter pub run build_runner build`. The code parsed, compiled and ran, but the data was not there, it was null.
	- so I went back to chat gpt giving it the errors I was getting and it saying that I had not used json serialisable, which I had and I had annotated the object with `@JsonSerializable 
		- TODO : this could be the problem ?
			I had not set (explicitToJson: true)` and the nested list did not have `@JsonKey(explicitToJson: true)`
	- it then went on to propose a different approach, manually coding the factory methods and the toJson() methods, which I did and it worked
	- a second converation this time with copilot looked like this :
		- in this factory ProductIndex.fromJson method, the '$' convention is not used and the mapping of json keys is done in models.dart, not models.g.dart, is this a failure to use json serialisable properly ?
		- The factory ProductIndex.fromJson method you're referring to is a common pattern used when manually implementing JSON serialization in Dart. This method takes a Map (from JSON) and returns a new instance of ProductIndex.

		- The json_serializable package automates this process by generating the fromJson and toJson methods for you. When using json_serializable, you typically don't need to manually implement these methods. Instead, you annotate your class with @JsonSerializable(), and the package generates the serialization code for you.

		- If you're seeing a manually implemented fromJson method in a project that also uses json_serializable, it could be a sign that the class was not properly annotated, or that the code generation step was not run after the class was annotated.

		- To fix this, you would need to:

		- Ensure the class is annotated with @JsonSerializable().
		- Run the code generation command (flutter pub run build_runner build for a one-time build, or flutter pub run build_runner watch for continuous builds).
		- However, it's also possible that the manual implementation was intentional. For example, the developer might have wanted to implement custom serialization logic that couldn't be handled by json_serializable. In this case, the manual implementation is not a mistake, but a deliberate choice.
	- the last point is the real kicker here, the ai has comprehended fully that there is a possible deliberate decision on the part of the developer ( the other ai ) that json_serialisable may not be able to cope with the data structure that was being worked upon and that this could be intentional where by a manual mapping of json is required
	- I kind of get the idea from years of wrangling with data that you should if you can, keep data modeling to simple patterns and the simplest of all and easiest to read and work with are objects that have simple primitives within them, strings, ints, bools, doubles, lists of these and maps of these but ideally not nested maps or lists of maps each with objects in them that subsequenlty have lists of maps with objects in them and so on
	- Whist I dont have anything as complicated as this, I do have 1 layer of nesting for a list of simple objects, where this pattern is often dealt with on its own as a simple list of simple objects
	- so for simpliciies sake, I may go back and refactore to have just a simple object with global values for the whole project and split off the list of object into a separate file
	- Whichever, I have somethign workin and can go back and refactor later, once end to end tests are back in place and I have the time to do it
	- The level of conversation and comprehenstion on the part of the ai, in this place, copilot is really rather breath taking and is illustrative of a programmer having a co-coder to work with, which is what I have been saying for a while now, that this is the future of programming, not the end of it, at least not just yet 
	- longer term though I think LLMs will master not just programming but architecture
	- one developement in this area that I have seen is #autogen by non other than #microsoft https://github.com/microsoft/autogen
		- what this does is to orchestrate agents, each acting as chat-gpt's talking to each other, each with a different skill set, to create a complete application
		- this is likely a use of AI that is not fully understood but a simple idea using complex models to create a complex system
		- it reminds me of harry hill
			- 

