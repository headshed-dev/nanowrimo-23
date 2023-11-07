- this to do with restul apis, nestjs is one of the most respected ( according to my reading so far ) restapi frameworks
	- it is nodejs, typscript and based on expressjs but also can do fastify, yet another
		- Fastify is **a web framework highly focused on providing the best developer experience with the least overhead and a powerful plugin architecture**. It is inspired by Hapi and Express and as far as we know, it is one of the fastest web frameworks in town.
		  id:: 65493270-0601-4e8d-8f79-26d580a58393
	- I think this fits in sort of with writings to do with monitoring as something not done yet is webcheck, I think I can use that name as they have now stopped using it entirely which used apache, cgi and ssl ( tls to you an me today ) plus further encryptions with PGP made it quite difficult for network security to read it- which is why they didnt like it in my opinion
	- seeing as I was reading the first O'Reilly text on restful APIs post to Y2K I think this pertinent as we were using 'GET' predominately with parameters to do much of what is available to RESTful GET, POST, et. al. in the 'modern day' so we were ahead of the curve on that one, thanks to Mr John Connor
	- in this video
		- by **Marius Espejo** who featured a playlist with [netninja nestjs crash course](https://www.youtube.com/watch?v=pcX97ZrTE6M&list=PL4cUxeGkcC9g8YFseGdkyj9RH9kVs_cMr)
			- {{video https://www.youtube.com/watch?v=nY0R7pslbCI}}
		- my interest with nestjs is renewed, having worked a project in Go and React that lacks any of this build pattern, let alone the capabilities that NextJS has built in from the get go
		- following from this is the series in flight by Dave Gray so far
			- part 1
				- {{video https://www.youtube.com/watch?v=juNVinepwKA&t=9s}}
			- part 2
				- {{video https://www.youtube.com/watch?v=otw0zQ0NSa4}}
		- as for hosting, I would go for my own vm, docker and local file store or encrypted buckets for current use cases but another interesting approach is to go for a variety of BaaS providers for which [back4app](https://blog.back4app.com/nest-js-hosting-providers/) themselves a BaaS summarize a number of options in this regard, some are even free forever tier, offering zero cost start up and possibly not-for-profit / charity options
- {{renderer :wordcount_}}
	- If your in any way aware of technology you will have heard the phrase API, meaning Application Program Interface and another closely associated RESTful API to quote AWS pages
		- Representational State Transfer (REST) is a software architecture that imposes conditions on how an API should work. REST was initially created as a guideline to manage communication on a complex network like the internet. You can use REST-based architecture to support high-performing and reliable communication at scale. You can easily implement and modify it, bringing visibility and cross-platform portability to any API system.
	- Other technologies merge and flux with this and add to a cloud of buzz words, tRPC is getting a lot of noise recently with headlines like
		- > Move Fast and Break Nothing.
		  End-to-end typesafe APIs made easy.
		  Experience the full power of TypeScript inference to boost productivity
		  for your full-stack application.
	- Graphql is another stating that
		- > GraphQL is a query language for APIs and a runtime for fulfilling those queries with your existing data. GraphQL provides a complete and understandable description of the data in your API, gives clients the power to ask for exactly what they need and nothing more, makes it easier to evolve APIs over time, and enables powerful developer tools.
	- While we're at it lets not forget gRPC from google
		- >A high performance, open source universal RPC framework
	- These are a snapshot of what I'm currently keeping an eye on that I bring to mind just now suffice to say there is always a lot of stuff going on.
	- I noticed, as did many bigger better minds than this little bear, that there are common issues we are faced with and patterns that tend to repeat themselves when building APIs.
		- We tend to pronounce API as the letters, A, P, I by the way, so you don't embarass yourself talking to a tech guru by saying 'whats an appy?' - a little amusing anectdote I recall from a respdected colleague remarking at this in regards to an amusing occurence in our work one day. I hope he is doing well, I get to meet a lot of bright, clever and dynamic people and he was one of them that shone brightly. When I'm feeling low or depressed I can recall good times and interactions with some in a busy work life, not always mind, but some stand out and that is one of them.
	- A framework that some use in environments developed using NodeJS called NestJS I like as it takes these ideas and formalises them in a way that we can adopt in our API projects that follow these well known, well trod paths.
	- I think that some of the attraction of becoming a programmer in particular but perhaps more generally, wanting to be seen as a 'wizz with computers' as I've heard and smiled with gritted teeth in the past is that there is a perception at least that when you become this mythical creature that you will have ultimate freedom to do things in a way that you see best and let your creative juices flow so to speak. I shudder at the thought of this. That the world is one seen through rosy colored g