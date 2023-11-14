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
	- type aliases can be used to make things more readable
		- for example `type MyType = {name: string, age: number}`
		- this can be used to make things more readable
		- for example `const x: MyType = {name: 'john', age: 30}`
		```javascript
			type Rgb = [number, number, number]

			function getRandomColor(): Rgb {
				let r = Math.floor(Math.random() * 255)
				let g = Math.floor(Math.random() * 255)
				let b = Math.floor(Math.random() * 255)

				return [r, g, b]
			}

			const color1: Rgb = getRandomColor()
			const color2: Rgb = getRandomColor()
			const color3: Rgb = getRandomColor()

			console.log(color1, color2, color3)

			// this looks like an interace but we have an = sign 
			// as this is a type alias
			type myUser = { name: string, age: number, email: string }

			const user1: myUser = {
				name: 'John',
				age: 30,
				email: 'jon@mail.com',
			}

			function formatUser(user: myUser) {
				return `>>> ${user.name} ${user.age} ${user.email}`
			}

			console.log(formatUser(user1))
		
		```
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
	- this is very nice
	- interfaces can do a lot more than say, types but it could be easy to think of them both as the same thing
	- TypeScript's interfaces and type aliases do have overlapping capabilities, but there are some differences:

	- Extension: Interfaces can be extended and merged, which is not possible with type aliases. This makes interfaces a good choice when you want to define a shape of an object and extend it later.

	```javascript
		interface Base {
		id: number;
		}

		interface Derived extends Base {
		name: string;
		}
	```

	which can't be done with a type alias
	- Declaration merging: Interfaces can be declared multiple times and they will be merged together. This is not possible with type aliases.

	```typescript
			interface SomeInterface {
			id: number;
			}

			interface SomeInterface {
			name: string; // This is okay
			}

			type SomeType = {
			id: number;
			};

			type SomeType = {
			name: string; // This will throw an error
			};

	```
	- Use with primitives and unions: Type aliases can represent primitive types, union types, intersection types, tuples, and other complex types, which is not possible with interfaces.
	```typescript
	type PrimitiveType = string;
	type UnionType = string | number;
	type TupleType = [string, number];
	```
	- Descriptive error messages: Interfaces tend to produce more descriptive error messages compared to type aliases.
	- In general, if you want to create a shape for an object-like structures, interfaces are a good choice. If you need to use more complex types or primitives, type aliases are the way to go.
	- type guards are a bit mad. You can use things like 'typeof' say in a function to check to see what the type of primitive you have passed and react accordingly, so if you have an id of mixed type using a union, you can then use programatic type guards to process this in a type safe way. If you dont, typescript will throw a wobbler. If your doing this with interfaces, it get even weirder, you need to define a 'type' attribute in your inteface which you can the access as 'type' in your function to do similar guards. At the moment, I cant see a useful use case for this, so will need to revisit this as this becomes more clear.
