# Binding Classes

1. in the style tag, create class call 'underline'

```js 
<style>
  .underline {
    text-decoration: underline;
  }
</style>
```

2. in the main tag, add h2 tag with created class name   
```js 
<main>
  <h2 class="underline" >Underline Text</h2>
</main>
```

## Dynamic Classes 

3. in the style tag, create two class call 'danger' and success

```js 
<style>
  .danger {
    color: red;
  }
  .success {
    color: olivedrab;
  }
</style>
```

4. in the script tag, create new variable call 'status' equal to 'danger'

```js 
<script>
 const status = 'danger';
</script>
```
5. in the main tag, create h2 tag with calss qual to 'status' and test this result with changing status value to 'danger' to 'success'
```js 
<main>
 <h2 class={status}>Status</h2>
</main>
```

6. show how to change class with condition in normal way  

```js 
<script>
 const isPromoted = false;
 const promoted = false;
</script>

<main>
  <h2 class={isPromoted ? 'promoted': ''}>Movie Title Noraml</h2>
  <h2 class:promoted={isPromoted}>Movie Title Special Directive</h2>
</main>
<h2 class:promoted>Movie Title Special Directive with shorthand way</h2>
</main>
<style>
  .promoted {
    font-style: italic;
  }
</style>

```