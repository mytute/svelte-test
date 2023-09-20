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

4. create copy of 'Card' component call 'Card2' inside component folder.

5. in 'Card2', add 3 parts slots with name attribute in following way.
Card2.svelte
```svelte
<div class="card"> 
    <div class="class-header">
        <slot name='header'></slot> 
    </div>
    <div class="class-content">
        <slot name='content'></slot>
    </div>
    <div class="class-footer">
        <slot name='footer'></slot>
    </div>
</div>
```

App.svelte
```svelte
<script>
  import Card2 from "./components/Card2.svelte";
</script>
<main>
	<Card2>
		<div slot="header"> <h2>this is header</h2></div>
		<div slot="content"> <img src="https://picsum.photos/200" alt=""> </div>
		<div slot="footer"> <button>View details</button></div>
	</Card2>
</main>
```

6. in above 'Card2' add '<hr>' tag before footer slot and render if footer is define on parent only  

Card2.svelte
```svelte
<div class="card"> 
    <div class="class-header">
        <slot name='header'></slot> 
    </div>
    <div class="class-content">
        <slot name='content'></slot>
    </div>
    {#if $$slots.footer } // add here
    <hr>
    <div class="class-footer">
        <slot name='footer'></slot>
    </div>
    {/if} / to here
</div>
```

### Slots props

we want to parent component to control how the child component wii render the content. 
we can use slots for this.

The task is how define print only 'firstName' or 'lastName' from the parent component. for this we can use slot prpos. 

NameList.svelte
```svelte
<script>
    const names = [
        {fitstName: 'samadhi', lastName: 'laksahan'},
        {fitstName: 'thi', lastName: 'pasi'},
        {fitstName: 'mala', lastName: 'rath'},
    ];
</script>
<main>
    {#each names as name (name)}
      <h2>{name.fitstName} {name.lastName}</h2>
    {/each}
</main>
```

7. in NameList component add slot inside loop and send values to parent component using slot props 

NameList.svelte
```svelte
<main>
    {#each names as name (name)}
      <slot name="hero" firstName={name.fitstName} lastName={name.lastName}/>
    {/each}
</main>
```

8. in App component controll order of the 'firstName' and 'lastName'.

App.svelte
```svelte
<main>
	<NameList>
		<h3 slot='hero' let:firstName let:lastName >
			{firstName} {lastName}
		</h3>
	</NameList>
	<NameList>
		<h3 slot='hero' let:firstName let:lastName >
			{lastName} {firstName} 
		</h3>
	</NameList>
</main>
```