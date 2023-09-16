# Binding Text

1. delete the props property in main.js file. 
2. in App.svelte file in the script tag define variable 'name'

```js 
const name = 'samadhi';
```
3. in the main tag open single curly braces to put above 'name' variable and see the result. 
```js 
<main>
	<h1>Hello {name}!</h1>
</main>
```

4. change 'name' variable above to 2+2 and see the result. 
```js 
<main>
	<h1>Hello {2+2}!</h1>
</main>
```