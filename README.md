# Form Handling

Capture user inputs
Inputs
Textareas
Single select dropdown control
Multi select control
Checkbox
Checkbox group
Radio   
Submit from data



### i
1. in style tag, add sytle for form and remove 'text-align: center'   
```svelte
<style>
  input + label {
		display: inline-flex;
	}
  main {
		/* text-align: center; */
	}
</style>
```

2. in script tag, create new object variable call 'formValues' contain form fields and it's initial values.
```js
<script>
   const formValues = {
	   name:''
   }
</script>
```  

3. in main tag, create label and input element inside form elements and bind input element with above formValues.name value.
```js
<main>
  	<form>
      <div>
        <label for="name">Name</label>
        <input type="text" name="" id="name" bind:value={formValues.name} />
	    </div>
	</form>
</main>
```  

4. in main tag.  show json values to show live updates on 'formValues' variable 
```js
<main>
	<div>
		<pre>
			{JSON.stringify(formValues, null, 2)}
		</pre>
	</div>
</main>
```  

4. show how input type change to number "type='number'" make changes json value type. show this is handle by svelte and not by vanilla js 
```js
<main>
	<div>
		<pre>
			{JSON.stringify(formValues, null, 2)}
		</pre>
	</div>
	<form>
		<div>
		 <label for="name">Name</label>
		 <input type="text" name="" id="name" bind:value={formValues.name} />
	  </div>
	</form>

</main>
``` 

5. show how to add textarea and bind with 'formValues' variable. 
```svelte
<script>
   const formValues = {
	 ...
   profile:''
   }
</script>
<main>

	<form>
    ....
		<div>
		 <label for="profile">Profile</label>
		 <textarea  id="profile" bind:value={formValues.profile} />
	  </div>
	</form>

</main>
``` 

6. show how to add dropdown and bind with 'formValues' variable.
<script>
   const formValues = {
	 ...
   country:''
   }
</script>
<main>

	<form>
    ...
		<div>
			<label for="country">Country</label>
			<select  id="country" bind:value={formValues.country}>
				<option value="">Select a contry</option>
				<option value="india">India</option>
				<option value="vietnam">Vietnam</option>
				<option value="singapore">Singapore</option>
			</select>
		</div>
	</form>

</main>
``` 

7. show how to add multiple dropdown and bind with 'formValues' variable.
<script>
   const formValues = {
	 ...
   jobLocation: []
   }
</script>
<main>

	<form>
    ...
		<div>
			<label for="job-location">Job Location</label>
			<select  id="job-location" bind:value={formValues.jobLocation} multiple>
				<option value="">Select a contry</option>
				<option value="india">India</option>
				<option value="vietnam">Vietnam</option>
				<option value="singapore">Singapore</option>
			</select>
		</div>
	</form>

</main>
``` 

8. show how to add single checkbox and bind with 'formValues' variable. (remote work)
<script>
   const formValues = {
	 ...
   remoteWork: false
   }
</script>
<main>

	<form>
    <!-- ... -->
    <div>
			<input  type="checkbox" id="remote-work" bind:checked={formValues.remoteWork} />
			<label for="remote-work">Open to remove work ?</label>
		</div>
	</form>

</main>
``` 

9. show how to add multiple checkbox and bind with 'formValues' variable. (skill set)
<script>
   const formValues = {
	 ...
   skillSet: []
   }
</script>
<main>

	<form>
    <!-- ... -->
    <div>
			<label for="skill-set">Skill set</label>

			<input  type="checkbox" id="html" value="html" bind:group={formValues.skillSet}/>
			<label for="html">Html</label>

			<input  type="checkbox" id="css" value="css" bind:group={formValues.skillSet}/>
			<label for="css">Css</label>

			<input  type="checkbox" id="javascript" value="javascript" bind:group={formValues.skillSet} />
			<label for="javascript">Javascript</label>
		</div>
	</form>

</main>
``` 

10. show how to add multiple radio and bind with 'formValues' variable. (skill set)
<script>
   const formValues = {
	 ...
   yearsOfExperience: ''
   }
</script>
<main>

	<form>
    <!-- ... -->
    <div>
			<label for="skill-set">Years Of Experience</label>

			<input  type="radio" id="0-2" value="0-2" bind:group={formValues.yearsOfExperience}/>
			<label for="0-2">0-2</label>

			<input  type="radio" id="3-5" value="3-5" bind:group={formValues.yearsOfExperience}/>
			<label for="3-5">3-5</label>

			<input  type="radio" id="6-10" value="6-10" bind:group={formValues.yearsOfExperience} />
			<label for="6-10">6-10</label>
		</div>
	</form>

</main>
``` 

11. show how to submit the form
add submit button end of the form tag
|preventDefault make not to refresh the page

<script>
   function submitForm(event){
	   console.log(formValues);
   }
</script>
<main>

	<form  on:submit|preventDefault={submitForm}>
    <!-- ... -->

    <button type="submit">submit</button>
	</form>

</main>
``` 