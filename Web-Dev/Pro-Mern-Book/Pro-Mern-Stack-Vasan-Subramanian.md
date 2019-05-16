# Pro Mern Stack Book

Full stack web dev with Mongo, Express, React and Node.

By: Vasan Subramian

## Introduction - Chapter 1

### What is MERN?

- Stack = combination of technologies
- MERN = Mongo, Express, React and Node.

### MERN Components

#### React

- Open source library created by facebook
- Innovative because it has a virtual dom so that it doesn't have to render all the webpage again
- React is **declarative** because you don't need to worry about DOM manipulation, react will do that for you. You just *declare* how the page is going to look.
- React is **component based**, all you do is contained in components
- React is **Isomorphic** which means it can be run on the server and in the client

#### Node.js

- Javascript which is runable without html

#### Express

- Web server framework
- In MERN express doesn't need a server-side template engine because the dynamic content generation is done on the client with react.

#### Mongo DB

- NOSql = non relational
- Data is denormalized (there can be duplicates)
- Schema less = You don't need a prescribed schema

### Tools and libraries

Other tools that might be needed to build the webapp

#### React Router

- React can only do the rendering and manage interactions between single components but fo transitioning between diferent views adn keeping the browser url in sync you use react router
- It is similar to what express does: usl is parsed, and based on its components an piece of code is associated with it.

#### React Bootstrap

- Special library of bootstrap for react

#### Webpack

- Good for modularizing
- Main function is to build clientside code into a bundle to deliver to the client

### Why MERN

- It uses javascript everywhere
- Node.js non-blocking I/O makes it really good for servers
- NPM Ecosistem

## Chapter 2: Hello World

### Server-less

```
<!DOCTYPE HTML>
<html>
<head>
	<meta charset="UTF-8" />
	<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.2.1/react.js"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/react/15.2.1/react-dom.js"></script>
	<script src="https://cdnjs.cloudflare.com/ajax/libs/babel-core/5.8.23/browser.min.js"></script>
</head>
<body>
	<div id="contents"></div> <!-- Here is where the react component is going to appear -->
	<script type="text/babel">
		var contentNode = document.getElementById('contents');
		var component = <h1>Hello World!</h1>; // Symple jsx component
		ReactDOM.render(component, contentNode); // render the component inside the div
	</script>
</body>
</html>
```
- In `var component = <h1>Hello World!</h1>;` we use JSX which actually gets conevrted to:
  - `var component = React.createElement('h1', null, 'Hello World!');`
  - In order to convert it we use the babel library, which is a browser based transformer
    - We are no actually going to use it much because it is not inteded to be used for production
  
**Excercises**
1. Remove type="text/babel" from the script. What happens, and can you explain why? remove the babel JavaScript library instead. What happens now?
   - The attribute "type=text/babel" on the script element indicates that the contents are JSX, as opposed to regular JavaScript, the default if you don’t specify a type. The babel compiler compiles all such script elements into JavaScript and injects it back. Removing either the babel compiler or the type attribute will cause the script not to be compiled into JavaScript and will cause errors on the JavaScript console.
2. Add a class to the h1 element (you will also need to define the class in a `<style> section within the <head> section.`) hint: Search for “how to specify class in jsx” on stackoverflow.com.
	- To specify a class in JSX, you need to use `className=<name> instead of class=<name>` as you would have done in HTML.
3. We used the minified version of babel, but not for react and react-dom. Can you guess why? Switch to the minified version and introduce a runtime error in react. For example, introduce a typo in the id of the content node so there is no place to mount the component. What happens?
	- A minified version of React hides or shortens runtime errors. A non-minified version gives full errors and helpful warnings as well.

### Server setup

#### nvm

- In order to always know which version of node you are using you instal *Node Version Manager*
- Then you just run the commmand
  - `nvm install node`

#### Project

- In order to create the project you use
  - `npm init`
- From now on you have a package and everything you install with npm can be saved in it

**Exercises NPM**
1. Find out what difference --save made. try uninstalling and re-installing express with and without this option. hint: the difference is in package.json.
	- The npm option --save causes the installation/uninstallation to be recorded under the dependencies section of package.json.
2. When was package.json created? If you can't guess, inspect the contents for a hint. Still can't figure out? Go back and redo your steps. Start with creation of the project directory, and look at the directory contents at each step.
	- package.json got created when we created the project using npm init. In fact, all of the responses to the prompts when we ran npm init were recorded in package.json.
3. Uninstall express. Now, just type npm install. What happens? add another dependency, mongodb, manually to package.json this time. Use version as “latest”. Now, type npm install. What happens? Uninstall mongodb, and use --save this time to affect package.json.
	- Running npm install without any further options or parameters causes all dependencies to be installed, by looking at package.json. Thus, you could add dependencies manually topackage.jsonandjustusenpm install.Thisgivesyou better control over which version of the package you want.
4. Use --save-dev instead of --save while installing a package. What difference do you see in package.json? What difference do you think it will make?
	- The option --save-dev adds the package in devDependencies instead of dependencies. The list of dev dependencies. Ths list of dev dependencias will not be installed in production, which is indicated by te environment varibale `NODE_ENV` being set to the string `production`.
5. Where do you think the packages files are installed? type npm ls --depth=0 to check all the currently installed packages. Clean up any packages you do not need.
	- Package files are installed under the directory node_modules under the project. npm ls lists all the packages installed, in a tree-like manner. --depth=0 restricts the tree depth to the top- level packages. Deleting the entire node_modules directory is one way of ensuring you start clean.