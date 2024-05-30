### Click anywhere on the map to get its lat lon.

Open your `map.js` file and Add the following leaflet code:

```javascript
var popup = L.popup();

function onMapClick(e) {
	popup.setLatLng(e.latlng).setContent("You clicked the map at " + e.latlng.toString()).openOn(map);
}
map.on('click', onMapClick);
```

### layercontrols.
This will show you how to group several layers into one, and how to use the layers control to allow users to easily switch different layers on your map.

<img src="images/layers Control.png">

```javascript
var osm = L.tileLayer('https://tile.openstreetmap.org/{z}/{x}/{y}.png', {
	attribution: '&copy; <a href="http://www.openstreetmap.org/copyright">OpenStreetMap</a>'
});

var osmHOT = L.tileLayer('https://{s}.tile.openstreetmap.fr/hot/{z}/{x}/{y}.png', {
	attribution: '&copy; <a href="https://www.openstreetmap.org/copyright">OpenStreetMap</a> contributors, Tiles style by <a href="https://www.hotosm.org/" target="_blank">Humanitarian OpenStreetMap Team</a> hosted by <a href="https://openstreetmap.fr/" target="_blank">OpenStreetMap France</a>'
});

var map = L.map('map', {
	center: [27.68723120070982, 85.32372326123497],
	zoom: 19,
	layers: [osm]
});

var baseLayers = {
	'OpenStreetMap': osm,
	'OpenStreetMap.HOT': osmHOT
};

var layerControl = L.control.layers(baseLayers).addTo(map);
```

Add google satellite image on the above.

Satellite:

```javascript
var googleSat = L.tileLayer('http://{s}.google.com/vt/lyrs=s&x={x}&y={y}&z={z}',{
        subdomains:['mt0','mt1','mt2','mt3']

layerControl.addBaseLayer(googleSat, 'Satellite Image');
```

Hybrid
```javascript
var googleHybrid = L.tileLayer('http://{s}.google.com/vt/lyrs=s,h&x={x}&y={y}&z={z}',{
        subdomains:['mt0','mt1','mt2','mt3']
});

layerControl.addBaseLayer(googleHybrid, 'Hybrid');
```

streets
```javascript
var googleStreets = L.tileLayer('http://{s}.google.com/vt/lyrs=m&x={x}&y={y}&z={z}',{
        subdomains:['mt0','mt1','mt2','mt3']
});

layerControl.addBaseLayer(googleStreets, 'streets');
```

Terrain
```javascript
googleTerrain = L.tileLayer('http://{s}.google.com/vt/lyrs=p&x={x}&y={y}&z={z}',{
        subdomains:['mt0','mt1','mt2','mt3']
});

layerControl.addBaseLayer(googleTerrain, 'Terrain');
```
