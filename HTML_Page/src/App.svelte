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


	/*h4 {
		counter-reset: detail;
		color: #228B22;
		text-align: left;
		font-size: 1.5em;
	}


	h4:before {
		counter-increment: composite;
     	content: counter(section) "." counter(sub-section) "." counter(composite) ". ";
	}*/


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

	/*.TwoCols {
		float: left; 
		text-align: left; 
		width: 50%;
		padding: 5px;
	}*/

	.row::after {
  		content: "";
  		clear: both;
  		display: table;
	}

	/*img {
		width: 500px;
		height: 333px;

		max-width: 50%;
		max-height: 33%;
    	height: auto;
    	width: auto\9;

		float: right;

		margin-top: 8px;
		margin-bottom: 10px;
  		margin-left: 0px;
  		margin-right: 0px;
	}*/


	a {
  		color: steelblue;
		text-decoration: underline;
	}


	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}
</style>


<main>
	<h1>COVID-19 & the MiBici Bike-Sharing System in Guadalajara</h1>
	<h1 style="font-size:2em">By: Clifford Cele</h1>

	
	<h2>Introduction</h2> <!-- NiceBikeDock -->

	<!--
	<div class='row'>
		<div class="TwoCols">
			<img src='../Images/NiceBikeDock.jpg' alt=""/>
		</div>
		<div class="TwoCols">
			<img src='../Images/NiceBikeDock.jpg' alt=""/>
		</div>
  	</div>
	-->
	
 	 <p> <a href="https://www.mibici.net/">MiBici</a> (MyBike) is Guadalajara's public bike sharing system in the state of Jalisco, Mexico. Created 
		 in 2014, the system has over 3,200 bikes and 300 stations available in the municipalities of Guadalajara, Zapopan, and Tlaquepaque. 
		 MiBici consists of a line of bikes that are locked into a network of docking stations throughout the municipalities. To use the bikes, one must
		 purchase a subscription. The bikes can be unlocked from one station and returned to any other station in the system. Bikes are available every 
		 day of the year from 05:00 AM to 00:59 AM and are designed to be used for an unlimited number of trips so long as each trip is less than 30 
		 minutes (on Sundays, this is 45 minutes). When bikes are used for periods of more than 30 minutes, additional charges are incurred.
		 The program acts as a complement or extension to other transportation systems in the area <a href="https://www.mibici.net/es/preguntas-frecuentes/">[MiBici FAQs]</a>.

		 <br><br>
    	 As the coronavirus disease 2019 (COVID-19) hit Mexico in 2020, the government announced a national lockdown which took place between 23 March 2020
		 and 30 May 2020, where all non-essential activities and in person education was suspended <a href="https://globalhealthsciences.ucsf.edu/sites/globalhealthsciences.ucsf.edu/files/mexico-covid-19-case-study-english.pdf">[UCSF IGHS]</a>. 
		 During this period and with the rise of social distancing as a measure to mitigate the spread of the disease, people seemed to turn to cycling
		 as a form of mobility and exercise. On 18 May 2020, Christina Goldbaum published the New York Times article <a href="https://www.nytimes.com/2020/05/18/nyregion/bike-shortage-coronavirus.html">“Thinking of Buying a Bike? Get Ready for a Very Long Wait” </a> 
		 where they discussed the shortage of bicycles available to purchase in the NYC area and the desire to be outside amidst the pandemic. 
		 Researchers Padmanabhan et al. (2021), studied the effects of the first wave of COVID-19 (March-June 2020) on bike sharing systems in three cities 
		 of the United States (US): NYC, Boston, and Chicago <a href="https://www.ncbi.nlm.nih.gov/pmc/articles/PMC7964246/">[article]</a>. They concluded 
		 that the number of bike trips were negatively impacted by the number of COVID‐19 cases, but trip durations increased. 
		 
		 <br><br>
		 As such, the goal of this project is to explore and visualize how cycling behaviors have changed in Guadalajara and its surrounding municipalities 
		 due to the COVID-19 pandemic (between 2019 and 2021????).
		
		<br>


	</p>


    <h2>Data Sources</h2>

	<h3>MiBici</h3>
	<p> (MUST CHANGE) The MiBici <a href="https://www.mibici.net/es/datos-abiertos/">open data</a> set contains 21,765,814 observations across 15 variables. Each observation represents a bike ride, and each variable (in BOLD) contains 
		information about the bike ride. (DISCUSS ADDED VARIABLES) Reverse geocoding was used in Python to obtain the full address, neighborhood, and municipality 
		of each station.

	</p>
	
	<div class="row">
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
	</div>
	
	<h3>COVID-19</h3>
	<p> The general directive of epidemiology for the Mexican government maintains a <a href="https://datos.covid-19.conacyt.mx/">dashboard</a> of COVID-19 data for the country. In this analysis, the daily 
		count of confirmed cases is used for the municipalities of interest.	
	</p>


	<h2>Research Questions</h2>

	<ol class="ListQuestions">
		<li>How has the number of trips taken changed pre and post COVID?</li>
		<p>This question is based on the study by Padmanabhan et al. (2021) who studied the effects of COVID-19 on bike sharing systems in three US cities. 
			The idea here is to compare biking trends to various waves of COVID-19 where cases changed drastically. 
			
			<br><br>
			- Three line plots: 1) avg # bike trips per day, 2) Covid cases, 3) avg trip duration<br>
			- need the option to see trips by municipality (radio button or dropdown menu) <br>
			- Line part of avg # daily bike trips and either: 1) the line is a heatmap/ warmer/colder colors = higher/lower covid cases, or 2) background color changes the same way as covid chases change 
		
		</p>



		<li>Has the average trip duration changed over time?</li>
		<p> The MiBici system is described to be used as a commuting option for people. With the lifestyle changes brought about by the COVID-19 pandemic,
			have people changed how they use the system? Perhaps MiBici is being used more as a leisure activity.
		
			<br><br>
			- RADIAL SPIDER CHART (like DataVoz course proj, each color will represent a year, will do it by week in ear) <br>
			- A Bar cart per year <br>
			- Flower plot like dataviz final proj?

		</p>



		<li>What times of day are most popular to use the MiBici system? </li>
		<p>This question is based on a <a href="https://toddwschneider.com/posts/a-tale-of-twenty-two-million-citi-bikes-analyzing-the-nyc-bike-share-system/">blog post</a> 
			by Todd W Schneider who analyzed the Citi Bike system in NYC. They created a plot of the average number of weekday Citi Bike trips by hour of day 
			between Manhattan and the outer boroughs. It illustrates that in the mornings there are more riders entering Manhattan than leaving, and the reverse 
			occurs in the afternoon; illustrating commuter patterns similar to rush hour (when people are heading to and from work/school).

			<br><br>
			- Radial Heatmap (one map per year will have grid of plots) <br>
		</p>



		<li>What are the most popular pairs of start/end stations?</li>
		<p> If MiBici is being used more and more for leisure post COVID-19, are the popular locations that users visit different from the ones they visited
			before the start of the pandemic?

			<br><br>
			- see word.doc, need some sort of map, would be interesting to info by Neighborhood & neighborhood-income (or # stations by neighborhood & income) <br>
			- Google direction lines for most popular trips, maybe just two maps: 1) pre-covid years, and 2) post-covid years

		</p>

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


	<h2>GitHub</h2>
	<p> The code for this project can be found <a href="https://github.com/cliffordcele/MiBici">here</a> on GitHub.
	</p>



</main>