---
layout: page
title: Map
---

<style>
  /* Always set the map height explicitly to define the size of the div
    * element that contains the map. */
  #map {
    /* height: 100%; */
    height: 400px;
  }
  /* Optional: Makes the sample page fill the window. */
  html, body {
    height: 100%;
    margin: 0;
    padding: 0;
    font-family: Arial, Helvetica, sans-serif;
  }
</style>

<div>
  <h4>Habitat Loss Dashboard - Niagara Region</h4>
  <ul>
    <li>The regions shown in red have been lost</li>
    <li>The regions shown in yellow are in imminent danger of being lost</li>
    <li>The regions shown in green still exist: enjoy them, protect them</li>
  </ul>
</div>
<div id="map"></div>
<script>

  // This example creates a simple polygon representing the Bermuda Triangle.
  // When the user clicks on the polygon an info window opens, showing
  // information about the polygon's coordinates.

  var map;
  var infoWindow;

  function initMap() {
    map = new google.maps.Map(document.getElementById('map'), {
      zoom: 9,
      center: {lat: 43.058079, lng: -79.289132},
      mapTypeId: 'terrain'
    });

    // Define the LatLng coordinates for the polygon.
    var triangleCoords = [
      {lat: 43.058079, lng: -79.289132},
      {lat: 43.158079, lng: -79.289132},
      {lat: 43.138079, lng: -79.339132},
      {lat: 43.088079, lng: -79.389132},
      {lat: 43.058079, lng: -79.289132}
    ];

    // Construct the polygon.
    var bermudaTriangle = new google.maps.Polygon({
      paths: triangleCoords,
      strokeColor: '#FF0000',
      strokeOpacity: 0.8,
      strokeWeight: 3,
      fillColor: '#FF0000',
      fillOpacity: 0.35
    });
    bermudaTriangle.setMap(map);

    // Add a listener for the click event.
    bermudaTriangle.addListener('click', showArrays);

    infoWindow = new google.maps.InfoWindow;
  }

  /** @this {google.maps.Polygon} */
  function showArrays(event) {
    // Since this polygon has only one path, we can call getPath() to return the
    // MVCArray of LatLngs.
    var vertices = this.getPath();

    var contentString = '<b>Hendershot Boulevard & Garner Road, Niagara Falls</b>' +
        '<br>Mature forests in 1934 would have been continually forested since at least the 1850’s - 1830’s making this a remnant of the original Carolinian forest.' +
        '<br><a href="/locations/hendershot-blvd.html">Read more</a>';

    // Replace the info window's content and position.
    infoWindow.setContent(contentString);
    infoWindow.setPosition(event.latLng);

    infoWindow.open(map);
  }
</script>
<script async defer
src="https://maps.googleapis.com/maps/api/js?key=AIzaSyC5PkHlWOsv37xAO4GlTRHnPQhkNvqIDDc&callback=initMap">
</script>
