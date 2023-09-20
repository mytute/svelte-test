# Slots, Named Slots and Slots props

### Slots    

1. create Card component inside 'component' folder. And pass 'content' to 'Card' component from 'App' component.  


here only passing only string value to child component.

App.svelte
```svelte
<script>
  import Card from "./components/Card.svelte";
</script>

<main>
  <Card content="child 001"/>
  <Card content="child 002"/>
</main>
```

Card.svelte
```svelte
<script>
    export let content;
</script>

<div class="card">{content}</div>

<style>
    .card {
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
        transition: 0.2s;
        padding: 16px;
        margin-bottom: 20px;
        width: 200px;
    }
    .card:hover{
        box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
    }
</style>
```


2. according to above example show how to pass html to the child component.

* in parent component make open-close tag of child component and between it add content.
* in child tag add slot tag instead of content.

App.svelte
```svelte
<main>
  <Card> Card Content </Card>
  <Card> <h2>Card Content</h2> </Card>
</main>
```

Card.svelte
```svelte
<div class="card"> <slot/> </div>

```

3. show how to add default content 

* make '<slot/>' tag to open close tag and add default content between it. 

App.svelte
```svelte
<main>
  <Card> Card Content </Card>
  <Card> <h2>Card Content</h2> </Card>
  <Card/>
</main>
```

Card.svelte
```svelte
<div class="card"> <slot>Default content</slot> </div>

```

### Named Slots 

* make multiple slots