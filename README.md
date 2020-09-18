# Info

The purpose of this project is to demonstrate a set of TypeScript design patterns in practice.
The project demonstrates how one can connect and use Google Maps API.

## parcel-bundler package

I will use a tool called `parcel-bundler`, that helps run TS in the browser:
`$ npm install -g parcel-bundler`

How parcel-bundler works:

- we will create in our project an index.html file
- inside **index.html** we will include a script tag for a file called **index.ts**
- we will feed **index.html** into parcel & parcel will compile **index.ts** to **index.js**

In order to start parcel:
`$ parcel .\index.html`

## faker package

The current project works with randomly generated data created with `faker` package:
`$ npm i faker`.

After installing and importing `faker` into a .ts file one could see the following error: ***Could not find a declaration file for module 'faker'.*** This is a warning that can appear frequently in TS projects.

Explanation:
- whenever we write TS code we can us JS libraries
- there is a caveat though: 
  - TS want to check the code, and it does so by the use of types
  - JS libraries do not have type information attached
- to fix the issues above TS has the idea of **type definition files**:
  - they act like adaptors between TS code and JS libraries: TS Code -> Type Definition File -> JS Library
  - they tell to the TS compiler all the available types available in the JS library
  - usually they are available when you install a JS library

NOTE: Usually all the **type definition files** for popular libraries are already publicly available. We can check this by reaching into a project called **Definitely Typed**. You can install the required file:
`$ npm i @types/{library name}`
example:
`$ npm i @types/faker`

## Exports

In TS there is the convention to avoid **default exports**.

```typescript
// In User.ts
export default 'Hello'; // try to avoid!!!
export class User { /* ... */ }

// In index.ts
import { User } from './User';
import greet from './User';
console.log(greet);
console.log(new User());
```

## Project set-up

We will add Google Maps support inside of our application:
- generate a Google Dev Project at https://console.developers.google.com/
- enable Google Maps support inside the project
- generate an API key
- add Google Maps script tag to our HTML file
- install a **type definition file** in order to make our TS code understand the structure of `googlemaps` library:
  - `npm i @types/googlemaps`

NOTE: In TS is not required that the class of an object implements an interface as long as it satisfies the interface structure. So `implements InterfaceName` can be omitted from the class definition. Still, explicitly implementing an interface can help TS point the source of an error when the interface structure changes. 
