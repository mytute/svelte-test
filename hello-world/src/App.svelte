<script>
   const formValues = {
	 name:'',
	 profile: '',
	 country:'',
	 jobLocation: [],
	 remoteWork: false,
	 skillSet: [],
	 yearsOfExperience:''
   }

   function submitForm(event){

	 console.log(formValues);
   }
</script>

<main>
	<div>
		<pre>
			{JSON.stringify(formValues, null, 2)}
		</pre>
	</div>
	<form on:submit|preventDefault={submitForm}>
		<div>
		 <label for="name">Name</label>
		 <input type="text" name="" id="name" bind:value={formValues.name} />
	    </div>
		<div>
		  <label for="profile">Profile</label>
		  <textarea  id="profile" bind:value={formValues.profile} />
		</div>
		<div>
			<label for="country">Country</label>
			<select  id="country" bind:value={formValues.country}>
				<option value="">Select a contry</option>
				<option value="india">India</option>
				<option value="vietnam">Vietnam</option>
				<option value="singapore">Singapore</option>
			</select>
		</div>

		<div>
			<label for="job-location">Job Location</label>
			<select  id="job-location" bind:value={formValues.jobLocation} multiple>
				<option value="">Select a contry</option>
				<option value="india">India</option>
				<option value="vietnam">Vietnam</option>
				<option value="singapore">Singapore</option>
			</select>
		</div>

		<div>
			<input  type="checkbox" id="remote-work" bind:checked={formValues.remoteWork} />
			<label for="remote-work">Open to remove work ?</label>
		</div>

		<div>
			<label for="skill-set">Skill set</label>

			<input  type="checkbox" id="html" value="html" bind:group={formValues.skillSet}/>
			<label for="html">Html</label>

			<input  type="checkbox" id="css" value="css" bind:group={formValues.skillSet}/>
			<label for="css">Css</label>

			<input  type="checkbox" id="javascript" value="javascript" bind:group={formValues.skillSet} />
			<label for="javascript">Javascript</label>
		</div>

		<div>
			<label for="skill-set">Years Of Experience</label>

			<input  type="radio" id="0-2" value="0-2" bind:group={formValues.yearsOfExperience}/>
			<label for="0-2">0-2</label>

			<input  type="radio" id="3-5" value="3-5" bind:group={formValues.yearsOfExperience}/>
			<label for="3-5">3-5</label>

			<input  type="radio" id="6-10" value="6-10" bind:group={formValues.yearsOfExperience} />
			<label for="6-10">6-10</label>
		</div>


        <button type="submit">submit</button>
	</form>

</main>

<style>
	input + label {
		display: inline-flex;
	}
	main {
		/* text-align: center; */
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
	}

	h1 {
		color: #ff3e00;
		text-transform: uppercase;
		font-size: 4em;
		font-weight: 100;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>