### Click anywhere on the map to get its lat lon.

Open your `map.js` file and Add the following leaflet code:

```javascript
var popup = L.popup();

function onMapClick(e) {
	popup.setLatLng(e.latlng).setContent("You clicked the map at " + e.latlng.toString()).openOn(map);
}
map.on('click', onMapClick);
```
