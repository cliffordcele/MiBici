<script>
	//export let name;

	// IMporting plots like svelte components
	//import Ds_1 from "./designs/design_1.svelte";
</script>


<style>
	main {
		counter-reset: section;
		text-align: center;
		padding: 1em;
		max-width: 240px;
		/*margin: 0 auto;*/
		margin-top: 10px;
		margin-bottom: 10px;
  		margin-left: 50px;
  		margin-right: 50px;
	}

	h1 {
		text-align: center;
		color: #228B22;
		text-transform: uppercase;
		font-size: 3em;
		font-weight: 100;
	}

 	h2 {
		counter-reset: sub-section;
		color: #228B22;
		text-align: left;
		font-size: 2em;
	}

	h2:before {
		counter-increment: section;
		content: counter(section) ". ";
	}

   	h3 {
		counter-reset: composite;
		color: #228B22;
		text-align: left;
		font-size: 1.5em;
	} 
	h3:before {
		counter-increment: sub-section;
     	content: counter(section) "." counter(sub-section) ". ";
	}

   	h4 {
		counter-reset: detail;
		color: #228B22;
		text-align: left;
		font-size: 1.5em;
	}

	h4:before {
		counter-increment: composite;
     	content: counter(section) "." counter(sub-section) "." counter(composite) ". ";
	}


	p {
		font-weight: normal;
		text-align: justify;
		width: 100%;
	}

	.ListQuestions {
		font-weight: bold;
		text-align: left;
	}

	.ThreeCols {
		float: left; 
		text-align: left; 
		width: 33%;
	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>


<main>
	<h1>COVID-19 & the MiBici Bike-Sharing System in Guadalajara, Mexico</h1>

	<h2>Introduction</h2>
	<p> MiBici (MyBike) is Guadalajara's public bike sharing system in the state of Jalisco, Mexico. Created in 2014, the system has over 3,200   
		bikes and 300 stations available in the municipalities of Guadalajara, Zapopan and Tlaquepaque. MiBici consists of a line of bikes that are locked 
		into a network of docking stations throughout the municipalities. The bikes can be unlocked from one station and returned to any other station in the system. 
		Bikes are available every day of the year from 05:00 AM to 00:59 AM, and are designed to be used (FREELY???) in intervals of 30 minutes. When bikes are used for
		periods of more than 30 minutes, charges are incurred. On Sundays, the first free time period is extended to 45 minutes. This makes the system ideal 
		for commutes, errands, to get to social engagements, etc.

		As the coronavirus disease 2019 (COVID-19) hit Mexico in 2020, city dwellers were forced into lockdown between March 
		2020-June 2020 where all schools were closed, and non-essential workers were required to stay home. During this period and with the rise of social 
		distancing as a measure to mitigate the spread of the disease, people seemed to turn to cycling as a form of mobility and exercise. 
		
		On the 18th of May 2020, Christina Goldbaum published the New York Times article “Thinking of Buying a Bike? Get Ready for a Very Long Wait” where they 
		discuss the shortage of bicycles available to purchase and the desire to be outside amidst the pandemic. Researchers Padmanabhan et al. (2021), studied the 
		effects of the first wave of COVID-19 (March-June 2020) on bike sharing systems in three cities of the United States (US): NYC, Boston, and Chicago. They concluded that the 
		number of bike trips were negatively impacted by the number of COVID‐19 cases, but trip durations increased. As such, the goal of this project is to explore 
		and visualize how cycling behaviors have changed in Guadalajara and its surrounding municipalities due to the COVID-19 pandemic (between 2019 and 2021????).
	</p>


    <h2>Data Sources</h2>

	<h3>MiBici</h3>
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.

	</p>


	<div class="ThreeCols">
		<strong>Individual Ride Data:</strong>
		<ul>
			<li>Trip ID</li>
			<li>User ID</li>
			<li>Gender</li>
			<li>Year of Birth</li>
			<li>Start Date/Time</li>
			<li>End Date/Time</li>
		</ul>
	</div>
	<div class="ThreeCols">
		<strong>Docking Station Data:</strong>
		<ul>
			<li>Station ID</li>
			<li>Station Name</li>
			<li>Municipality</li>
			<li>Latitude</li>
			<li>Longitude</li>
			<li>Docking Status (in/not in service)</li>
		</ul>
	</div>
	<div class="ThreeCols">
		<strong>Additional Station Data:</strong>
		<ul>
			<li>Address</li>
			<li>Municipality</li>
			<li>Neighborhood</li>
			<br>
			<br>
			<br>
			
		</ul>
	</div>
	
	<h3>COVID-2019 Epidemiology</h3>
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.
		

	</p>


	<h2>Research Questions</h2>

	<ol class="ListQuestions">
		<li>How has the number of trips taken changed pre and post COVID?</li>
		<p>This question is a continuation of the study by Padmanabhan et al. (2021) who studied the effects of COVID-19 on bike sharing systems in three US cities. 
			The idea here is to compare biking trends to the waves of COVID-19 where cases increased drastically.
		</p>

		<li>Have trip durations changed over time?</li>
		<p></p>

		<li>What times of day are most popular to use the MiBici system? </li>
		<p>This question is based on a blog post by Todd W Schneider who analyzed the Citi Bike system in NYC. They created a plot of the average number of weekday 
		    Citi Bike trips by hour of day between Manhattan and the outer boroughs. It illustrates that in the mornings there are more riders entering Manhattan than 
			leaving, and the reverse occurs in the afternoon, illustrating commuter patterns similar to rush hour (when people are heading to work/school).
		</p>

		<li>What are the most popular pairs of start/end stations?</li>
		<p></p>

		</ol>





	<h2>Results</h2>

	<h3>Question 1</h3>
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.
	</p>
	<!-- Must import plots with code below in script section (like importing svelte components)
	<Card><Ds_1 /></Card> -->
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.
	</p>


	<h3>Question 2</h3>
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.
	</p>

	<h3>Question 3</h3>
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.
	</p>

	<h3>Question 4</h3>
	<p> The Citi Bike dataset contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride.
	</p>

</main>