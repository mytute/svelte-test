# Binding Text

1. create new variable call "channel" and define string value with html tag

```js 
const channel = '<b>samadhi</b>';
```
3. in the main tag open single curly braces to put above 'name' variable with "@html" prefix and see the result. 
```js 
<main>
    <div>{channel}</div>
	<div>{@html channel}</div>
</main>
```

4. create new variable call "hack" to vulnerability example of html binding.    
```js 
const hack = `<a href="#" onclick="alert('you have been hacked')" >Win a prize!</a>`;
```
```js 
<main>
	<div>{@html hack}</div>
</main>
```




