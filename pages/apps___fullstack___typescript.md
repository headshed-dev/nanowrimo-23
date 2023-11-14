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