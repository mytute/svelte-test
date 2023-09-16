# Binding Attributes

1. in the script tag, create "headingId" variable with value of attribute "heading" 

```js 
const headingId = 'heading';
```
2. in the main tag with open single curly braces, put above 'headingId' variable as tag id. 
```js 
<main>
	<h2 id={headingId} >This is heading</h2>
</main>
```

3. show that it is possible to put id directly with single curly braces. and check the result in inspect window on browser.     
```js 
<script>
const id = 'heading';
</script>
<main>
	<h2 {id} >This is heading</h2>
</main>
```

4 show boolan attribute false value not showing on the tag but if value true it will show on the tag.

```js 
<script>
const disabled = true;
</script>
<main>
	<button {disabled} >Bind</button> // can see on the tag
</main>
```
```js 
<script>
const disabled = flase;
</script>
<main>
	<button {disabled} >Bind</button> // can't see on the tag
</main>
```