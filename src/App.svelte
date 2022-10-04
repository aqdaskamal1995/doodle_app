<style>
	.demo-widget {
	  background: #f1f1f1;
	  height: 100%;
	  width: 100%;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	}
	.demo-widget-total{
	  background:white;
	  height: 100%;
	  width: 100%;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	}
	.widget_yes{
	  background:  #c6f7cf;
	  height: 100%;
	  width: 100%;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  opacity: 0.5;

	}
	.widget_need{
	  background: #ffef98;
	  height: 100%;
	  width: 100%;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  opacity: 0.5;
	}
	.widget_no{
	  background: #ffc8c8;
	  height: 100%;
	  width: 100%;
	  display: flex;
	  justify-content: center;
	  align-items: center;
	  opacity: 0.5;
	}
	
	.demo-container {
	  max-width: 100%;;
	  width: 100%;
	  margin-top: 200px;
	  margin-left: 200px;
	}
	.buttons{
	grid-template-columns: repeat(4, 1fr);
	display: flex;
	margin-left: 10px;
  	flex-wrap: wrap;
  	gap: 20.75px;
	margin-bottom:20px;
	margin-top:20px;
	}

	.Headings{
	grid-template-rows: repeat(6, 1fr);
	display: flex;
	}

	.button_no{
    height:50px;
    width:360px;
	background-color:#ffc8c8;
	}
	.button_need{
    height:50px;
    width:360px;
	background-color:#ffef98;
	}
	.button_yes{
    height:50px;
    width:360px;
	background-color: #c6f7cf;
	}
	.date_heading{
		margin-top: 50px;
		margin-left: 0px;
	}
	.date-heading{
		margin-top: 200px;
	}
	.user-select-title{
		width: 170px;
		height: 50px;
	}
	.submit-user-form{
		grid-template-columns: repeat(5, 1fr);
		display: grid;
		margin-top: 80px;
		max-width: 800px;
		margin-left: 350px

	}
	.heading_webpage{
		margin-bottom: 0px;
		margin-top: 150px;
		text-align: center;
	}

</style>

<div>
	<h1 class=heading_webpage>
		Meeting Scheduler!
	</h1>
	<div class=demo-container>
	  <Grid bind:items={items_dates} rowHeight={100} let:item let:dataItem {cols}>
		<div class=demo-widget>{dataItem.date}</div>
	  </Grid>

	  <Grid bind:items={items_num_part} rowHeight={100} let:item let:dataItem {cols}>
		<div class=demo-widget-total>{dataItem.num_part}</div>
	  </Grid>

	  
	  <div class='buttons'>
		<div class = user-select-title>You</div>
		<button class={button_state[0]} id = 0  on:click={() => change_state_button(0)}>{date_state[0]}</button>
		<button class={button_state[1]} id = 1  on:click={() => change_state_button(1)}>{date_state[1]}</button>
		<button class={button_state[2]} id = 2  on:click={() => change_state_button(2)}>{date_state[2]}</button>
		<button class={button_state[3]} id = 3  on:click={() => change_state_button(3)}>{date_state[3]}</button>

	</div>

	  <Grid bind:items={items_person_a} rowHeight={60} let:item let:dataItem {cols}>
		<div class={fetch_widget_class(dataItem.availability)}>{dataItem.availability}</div>
	  </Grid>


	  <Grid bind:items={items_person_b} rowHeight={60} let:item let:dataItem {cols}>
		<div class={fetch_widget_class(dataItem.availability)}>{dataItem.availability}</div>
	  </Grid>


	  <Grid bind:items={items_person_c} rowHeight={60} let:item let:dataItem {cols}>
		<div class={fetch_widget_class(dataItem.availability)}>{dataItem.availability}</div>
	  </Grid>

	  <div class = submit-user-form>
		<label for="Name">Name:</label>
		<input type="text" id="name" name="Name"><br><br>
		<label for="email">Email:</label>
		<input type="text" id="email" name="email"><br><br>
		<button class=submit on:click={() => alert('Form has been submited')}>Submit</button>
	  </div>
	  	
	  
	  
	</div>
</div>
	
	<script>
	// 5 Columns and 6
	import Grid from "svelte-grid";
	import gridHelp from "svelte-grid/build/helper/index.mjs";

	
	const id = () => "_" + Math.random().toString(36).substr(2, 9);
	// defining a variable which stores the default state of users choice whether they are available or not
	let date_state = ['No','No','No','No']
	let button_state = ["button_no", "button_no", "button_no", "button_no"]

	let items_headings = [
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 2,
		  fixed: true,
		}),
		heading: 'Date',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 2,
		  fixed: true,
		}),
		heading: 'Total',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 2,
		  fixed: true,
		}),
		heading: 'Your choice',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 2,
		  fixed: true,
		}),
		heading: 'Adam',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 2,
		  fixed: true,
		}),
		heading: 'Anna',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 2,
		  fixed: true,
		}),
		heading: 'Daniel',
	  },
	
	  

	];


	let items_field_names = [
	  {
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 1,
		  h: 2,
		}),
		id: id(),
		date: '18 October 10:00 am - 10:30 am',
		
	  },
	
	  {
		6: gridHelp.item({
		  x: 0,
		  y: 1,
		  w: 1,
		  h: 2,
		}),
		id: id(),
		date: '19 October 10:00 am - 10:30 am'
	  },

	  {
		6: gridHelp.item({
		  x: 0,
		  y: 2,
		  w: 1,
		  h: 2,
		}),
		id: id(),
		date: '20 October 10:00 am - 10:30 am'
	  },

	  {
		6: gridHelp.item({
		  x: 0,
		  y: 3,
		  w: 1,
		  h: 2,
		}),
		id: id(),
		date: '21 October 10:00 am - 10:30 am'
	  },


	];
	
	let items_dates = [


	  {
		6: gridHelp.item({ 
		  x: 0.5,
		  y: 0,
		  w: 1,
		  h: 2,
		  fixed: true,
		}),
		id: id(),
		date: '18 October 10:00 am - 10:30 am',
	  },
	
	  {
		6: gridHelp.item({
		  x: 1.5,
		  y: 0,
		  w: 1,
		  h: 2,
		  fixed: true,
		}),
		id: id(),
		date: '19 October 10:00 am - 10:30 am',
	  },

	  {
		6: gridHelp.item({
		  x: 2.5,
		  y: 0,
		  w: 1,
		  h: 2,
		  fixed: true,
		}),
		id: id(),
		date: '20 October 10:00 am - 10:30 am',
	  },

	  {
		6: gridHelp.item({
		  x: 3.5,
		  y: 0,
		  w: 1,
		  h: 2,
		  fixed: true,
		}),
		id: id(),
		date: '21 October 10:00 am - 10:30 am',
	  },


	];

	let items_num_part = [
		
		{
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 1,
		  fixed: true,
		}),
		num_part: 'Total (yes and if need be)',
	  },

	  {
		6: gridHelp.item({ 
		  x: 0.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		num_part: '3'
	  },
	
	  {
		6: gridHelp.item({
		  x: 1.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		num_part: '1'
	  },

	  {
		6: gridHelp.item({
		  x: 2.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		num_part: '1'
	  },

	  {
		6: gridHelp.item({
		  x: 3.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		num_part: '2'
	  },


	];

	let items_select = [
	  {
		6: gridHelp.item({ 
		  x: 0.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  max: { w: 1, h: 1 },
		}),
		id: 1,
		state: 'No'
	  },
	
	  {
		6: gridHelp.item({
		  x: 1.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  max: { w: 1, h: 1 },
		}),
		id: 2,
		state: 'No'
	  },

	  {
		6: gridHelp.item({
		  x: 2.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  max: { w: 1, h: 1 },
		}),
		id: 3,
		state: 'No'
	  },

	  {
		6: gridHelp.item({
		  x: 3.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  max: { w: 1, h: 1 },
		}),
		id: 4,
		state: 'No'
	  },


	];

	let items_person_a = [

		{
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 1,
		  fixed: true,
		}),
		availability: 'Adam',
	  },

	  {
		6: gridHelp.item({ 
		  x: 0.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'Yes' 
	  },
	
	  {
		6: gridHelp.item({
		  x: 1.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'Yes' 
	  },

	  {
		6: gridHelp.item({
		  x: 2.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'No' 
	  },

	  {
		6: gridHelp.item({
		  x: 3.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'If need be' 
	  },


	];

	let items_person_b = [
		{
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 1,
		  fixed: true,
		}),
		availability: 'David',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0.5,
		  y: 0,
		  w: 1,
		  h: 1,
		   fixed: true,
		}),
		id: id(),
		availability: 'If need be' 
	  },
	
	  {
		6: gridHelp.item({
		  x: 1.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'No' 
	  },

	  {
		6: gridHelp.item({
		  x: 2.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'No' 
	  },

	  {
		6: gridHelp.item({
		  x: 3.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'Yes' 
	  },


	];

	let items_person_c = [
		{
		6: gridHelp.item({ 
		  x: 0,
		  y: 0,
		  w: 0.5,
		  h: 1,
		  fixed: true,
		}),
		availability: 'Anna',
	  },
	  {
		6: gridHelp.item({ 
		  x: 0.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'If need be' 
	  },
	
	  {
		6: gridHelp.item({
		  x: 1.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'No' 
	  },

	  {
		6: gridHelp.item({
		  x: 2.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'Yes' 
	  },

	  {
		6: gridHelp.item({
		  x: 3.5,
		  y: 0,
		  w: 1,
		  h: 1,
		  fixed: true,
		}),
		id: id(),
		availability: 'No' 
	  },


	];
	
	const cols = [
	  [50, 6],
	];

	function change_state_button(button_id){
		//Takes button id and changes state every time the button is clicked 

		if(date_state[button_id]=='No')
		{
			date_state[button_id]='If need be'
			button_state[button_id]='button_need'
		}
		else if (date_state[button_id]=='If need be')
		{
			date_state[button_id]='Yes'
			button_state[button_id]='button_yes'

		}
		else if (date_state[button_id]=='Yes')
		{
			date_state[button_id]='No'
			button_state[button_id]='button_no'
		}

	}
	function fetch_widget_class(availability){
		// Takes the availability for each user and returns the appropriate class name for element for css styling
		if (availability == 'No'){
			return 'widget_no'
		}
		else if (availability=='If need be'){
			return 'widget_need'
		}
		else if (availability == 'Yes'){
			return 'widget_yes'
		}
	}
	</script>