# jQuery Use Zip Code To Lookup City & State

The following code does the following: 
- Presents a simple form wherein the user inputs a zip code
- jQuery is used to make an ajax request to Google's map api based upon the zip code
- Based on the zip code information the City, State, Latitude, and Longitude data is returned

Required Dependicies Include: 
- Google Maps API: ```<script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=true"></script>```
- jQuery: ```<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>```

***

### Code
```html
<!DOCTYPE html>
<html lang="en">
	<head>
		<meta charset="UTF-8" />
		<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1"> 
		<meta name="viewport" content="width=device-width, initial-scale=1.0"> 
		<title>Zip Code Lookup</title>
		<script type="text/javascript" src="http://maps.google.com/maps/api/js?sensor=true"></script>
		<script type="text/javascript" src="https://ajax.googleapis.com/ajax/libs/jquery/1.11.2/jquery.min.js"></script>
		
		<style>
			#wrapper {width: 400px; margin: 10px auto;}
			form {width: 225px;}
			form label {display: block; margin-bottom: 5px;}
			form span.label {display: inline-block; width: 75px; text-align: right;}
		</style>
	</head>
	<body>
		<div id="wrapper">
			<form id="location-form" method="GET">
				<label>
					<span class="label">Zip Code</span> 
					<input id="zip" name="zip" type="text" />
				</label>
				<br/>
				<div id="location-data">
					<label>
						<span class="label">City</span>
						<input id="city" name="city" type="text" />
					</label>
					<br/>
					<label>
						<span class="label">State</span>
						<input id="state" name="state" type="text" />
					</label>
					<br/>
					<label>
						<span class="label">Longitude</span>
						<input id="lng" name="lng" type="text" />
					</label>
					<br/>
					<label>
						<span class="label">Latitude</span>
						<input id="lat" name="lat" type="text" />
					</label>
				</div>
				<!-- end #location-data -->
				<hr>
				
				<input type="submit" value="Submit">
			</form>
		</div>
		<script>
			// Example Google Geocode JSON Data - https://maps.googleapis.com/maps/api/geocode/json?address=23188
			
			/**
			* Hide the additional location data fields because they are empty
			* until the jQuery ajax request returns the location information
			*/
			$('#location-data'). hide();
            
            // Execute the following lookup code when the #zip input field loses focus
			$("#zip").blur(function() {
				
				// Make sure the zip is 5 char long
				if( $(this).val().length === 5 ) {
					
					// Display the additional location information
					$('#location-data').show('slow');
					
					// Set variables
					var city = $("#city");
					var state = $("#state");
					var longitude = $('#lng');
					var latitude = $('#lat');
									
					$.getJSON(
						"https://maps.googleapis.com/maps/api/geocode/json?",
						{	
							/**
							* Build Google Geocode Query
							* Append 'address' key and zip code input via (this.input) to the url
							*/
							address: this.value 
						}, 
						function(response) {
						    /**
						    * The commented code can be used to ensure that there are actual values
						    * for each of the returned values: city, state, longitude, and latitude
						    */
							//if (!city.val() && response && response.results.length && response.results[0].address_components[1].short_name) {
								city.val(response.results[0].address_components[1].short_name);
							//}
							//if (!state.val() && response && response.results.length && response.results[0].address_components[2].short_name) {
								state.val(response.results[0].address_components[2].short_name);
							//}
							//if (!longitude.val() && response && response.results.length && response.results[0].geometry.location.lat) {
								longitude.val(response.results[0].geometry.location.lat);
							//}
							//if (!latitude.val() && response && response.results.length && response.results[0].geometry.location.lng) {
								latitude.val(response.results[0].geometry.location.lng);
							//}
						} // end function
					) //end $.getJSON
				}
			});
			
		</script>
	</body>
</html>
```
