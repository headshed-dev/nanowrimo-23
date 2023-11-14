- {{renderer :wordcount_}}
	- declaring types in typescript is straightforward and can often be done with inference
		- for example `const x = 3` will infer that x is a number
	- typescript has a lot of built in types
		- `string`, `number`, `boolean`, `object`, `array`, `tuple`, `enum`, `any`, `void`, `null`, `undefined`, `never`, `unknown`
	- typescript also has a lot of built in utility types
		- `Partial`, `Required`, `Readonly`, `Record`, `Pick`, `Omit`, `Exclude`, `Extract`, `NonNullable`, `Parameters`, `ConstructorParameters`, `ReturnType`, `InstanceType`, `ThisParameterType`, `OmitThisParameter`, `ThisType`
		- one such, 'readonly', can be used to make things immutable
			- for example:
			```typescript
				type MyType = {
					name: string;
					age: number;
				};

				const person: Readonly<MyType> = {
				name: 'John',
				age: 30
				};

				// This will cause an error
				person.age = 31;
			```
		- declaring a variable as a string or number or boolean is straightforward
			- for example `const x: string = 'hello'`
		- declaring an array is straightforward
			- for example `const x: string[] = ['hello', 'world']`
		- declaring an object is straightforward
			- for example `const x: {name: string, age: number} = {name: 'john', age: 30}`
		- and so forth, but inference can be used if this makes things too verbose however, by declaring types in this manner can serve to document the code
	- inerfaces in typescript are where things get a bit more interesting, allowing us to structure objects in a predictable way and enforcing the schema if you would of objects and objects that use other objects, for example, here is an example of an author object, used with a posts object that uses the author and a function that processes all of this
	- ```typescript
		interface Author {
			name: string;
			email: string;
			phone: string;
		}

		const author: Author = {
			name: 'John',
			email: 'jon.doe@mail.com',
			phone: '1234567890'
		}

		console.log(author)

		interface Post {
			title: string;
			body: string;
			created: Date;
			author: Author;
		}

		const post: Post = {
			title: 'My awesome post',
			body: 'This is the body',
			created: new Date(),
			author: author,
		}

		function createPost(post: Post) {
			console.log(`post title: ${post.title} created at ${post.created} by ${post.author.name} email: ${post.author.email}`)
		}

		createPost(post)

		let posts: Post[] = []

		posts.push(post)


		let anotherPost: Post = {
			title: 'Another post',
			body: 'This is anoher post',
			created: new Date(),
			author: author,
		}

		posts.push(anotherPost)

		console.log(posts)
	
	```