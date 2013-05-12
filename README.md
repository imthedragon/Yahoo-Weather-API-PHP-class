# Yahoo Weather API PHP Class
## A PHP class for the Yahoo! Weather API
This PHP class gives you full control over the weather conditions and other data provided by Yahoo!'s Weather API. You can choose, for example, if the temperature is shown with or withouts its unit. Full weather or title descriptions from Yahoo! are left out intentionally.

## Usage
Include the YahooWeather.class.php file in your script. Then simply create an instance of the `YahooWeather` class. To use this class, you have to supply a `Yahoo! Where On Earth ID` [(WOEID)](http://developer.yahoo.com/geo/geoplanet/guide/concepts.html).
You can then use the following class functions to access the properties of the object:

### Weather conditions
- `getTemperature($showunit = true)` Returns the current temperature. Use the $showunit boolean parameter to show or hide the specified unit ( *°F* or *°C* ).
- `getTemperatureUnit()` Returns the plain temperature unit without numbers or symbols ( *F* or *C* ).
- `getConditionCode()` Yahoo provides a unique [code](http://developer.yahoo.com/weather/#codes) for every possible weather condition. You can use this e.g. for your own weather icons, condition translations, etc.
- `getDescription()` Returns a textual description of conditions, for example, *Sunny*.

### Location 
- `getLocationCity()` Returns the city of the current location.
- `getLocationCountry()` Returns the country of the current location.
- `getLocationRegion()` Returns the region or territory of the current location, if given.
- `getLocationState()` Returns the state of the current location, if given. Note: This gives the identical result as `getLocationRegion()`! Although Yahoo does not differentiate states, regions or territories in their results, this name might be more intuitive for use with U.S. states.
- `getLocationLatLong()` Returns the latitude and longitude of the location, e.g. *50.94, 6.96*.

### Wind
- `getWindSpeed($showunit = true, $decimals = 2, $separator = '.')` Returns the wind speed. Use the $showunit boolean parameter to show or hide the specified unit (*mph* or *km/h*). Use the $decimals integer parameter to set the number of decimals. Use the $separator string parameter to set the separator character.
- `getWindDirection($showunit = true)` Returns the wind direction in degrees. Use the $showunit boolean parameter to show or hide the specified unit ( *°* ).
- `getWindDirectionCardinal()` Returns the Cardinal wind direction, e.g. *NNE* for *North North-East*.
- `getWindChill($showunit = true)` Returns the current wind chill temperature. Use the $showunit boolean parameter to show or hide the specified unit ( *°F* or *°C* ).

### Atmosphere
- `getHumidity($showunit = true)` Returns the relative humidity. Use the $showunit boolean parameter to show or hide the specified unit ( *%* ).
- `getPressure($showunit = true)` Returns the barometric pressure. Use the $showunit boolean parameter to show or hide the specified unit ( *in* or *mb* ).
- `getPressureState()` Returns the state of the barometric pressure as integer - steady (0), rising (1), or falling (2).
- `getVisibility($showunit = true)` Returns the visibility distance. Use the $showunit boolean parameter to show or hide the specified unit ( *mi* or *km* ).

### Astronomy
- `getSunrise($time_format = 'g:i a')` Returns the sunrise time at the given location. Use the $time_format parameter to format the output.
- `getSunset($time_format = 'g:i a')` Returns the sunset time at the given location. Use the $time_format parameter to format the output.

### Service
- `getYahooURL()` Yahoo!'s Terms of Use ask to provide attribution to Yahoo! Weather Service in connection with the use of their weather feed. To do so, you can easily link back to Yahoo!'s weather service site, where you can also find a 5 day forecast for the current location.
- `getYahooIcon()` Returns the html image tag for the weather condition icon, which is used by Yahoo! and Weather.com. I don't know, if grabbing the image out of context is fine for Yahoo, so I suggest to use your own icons and use this one for testing purposes only.
- `getLastUpdated($date_format = 'D, d M Y g:i a e') ` Returns the date, the weather information was last updated. Use the $date_format parameter to format the output.
- `getTTL()` Returns how long in minutes the weather data should be cached.

### Forecast
- `getForecastTodayLow($showunit = true)` Returns the forecasted low temperature for today. Use the $showunit boolean parameter to show or hide the specified unit ( *°F* or *°C* ).
- `getForecastTodayHigh($showunit = true)` Returns the forecasted high temperature for today. Use the $showunit boolean parameter to show or hide the specified unit ( *°F* or *°C* ).
- `getForecastTodayConditionCode()` Yahoo provides a unique [code](http://developer.yahoo.com/weather/#codes) for every possible weather condition. You can use this e.g. for your own weather icons, condition translations, etc.
- `getForecastTodayDescription()` Returns a textual description of conditions, for example, *Sunny*.
- `getForecastTodayDate($date_format = 'd M Y')`: Returns today's date, used in the forecast data. Use the $date_format parameter to format the output of the date.

- `getForecastTomorrowLow($showunit = true)` Returns the forecasted low temperature for tomorrow. Use the $showunit boolean parameter to show or hide the specified unit ( *°F* or *°C* ).
- `getForecastTomorrowHigh($showunit = true)` Returns the forecasted high temperature for tomorrow. Use the $showunit boolean parameter to show or hide the specified unit ( *°F* or *°C* ).
- `getForecastTomorrowConditionCode()` Yahoo provides a unique [code](http://developer.yahoo.com/weather/#codes) for every possible weather condition. You can use this e.g. for your own weather icons, condition translations, etc.
- `getForecastTomorrowDescription()` Returns a textual description of conditions, for example, *Sunny*.
- `getForecastTomorrowDate($date_format = 'd M Y')` Returns tomorrow's date, used in the forecast data. Use the $date_format parameter to format the output of the date.

### Example
	<?php
	include 'YahooWeather.class.php';

	// create an instance of the class with L.A.'s WOEID
	$weather = new YahooWeather(2442047, 'f');
	$temperature = $weather->getTemperature();
	$city = $weather->getLocationCity();
	$country = $weather->getLocationCountry();
	$forecast = $weather->getForecastTomorrowHigh();
	echo "It is now $temperature in $city, $country. ";
	echo "Tomorrow's temperature will reach a maximum of $forecast. ";
	?>

## Requirements
Requires PHP 5.0 or newer with libxml and libcurl enabled.

## License
©2013, Marcel Fetten

[MIT License](http://opensource.org/licenses/mit-license.php) 

[Yahoo! Terms of Use](http://developer.yahoo.com/weather/#terms) 
 
**Please be aware that the Yahoo! Weather API may only be used by individuals and non-profit organizations for personal, non-commercial uses.**

## Help
For bugs or enhancements, feel free to either raise an issue or pull request in GitHub.