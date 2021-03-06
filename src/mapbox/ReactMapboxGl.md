## onStyleLoad

- https://github.com/alex3165/react-mapbox-gl/issues/22
- onStyleLoad callback is now called before childrens components are rendered https://github.com/alex3165/react-mapbox-gl/blob/master/CHANGELOG.md
- To use the original Mapbox API use onStyleLoad property, the callback function will receive the map object as a first arguments, then you can add your own logic alongside react-mapbox-gl. https://github.com/alex3165/react-mapbox-gl/blob/master/docs/API.md

## center map with offset and padding

- a LngLatBounds object or LngLatBoundsLike is "south west", "north east". LngLat is long then lat, so the full bounds like object will be [[west, south], [east, north]] https://github.com/mapbox/mapbox-gl-js/issues/4281#issuecomment-280212578
- https://stackoverflow.com/questions/35586360/mapbox-gl-js-getbounds-fitbounds/35715102#35715102
- The LngLatBounds constructor (and convert), can take an array of four coordinate as well https://github.com/mapbox/mapbox-gl-js/issues/5249
- https://www.mapbox.com/mapbox-gl-js/api/#map#fitbounds
- https://www.mapbox.com/mapbox-gl-js/api/#lnglatbounds

```jsx
    let boundsArray = BHUTAN_BOUNDS;
    let fitBoundsOptions = { offset: [sidebarWidth / 2, 0] }; // eslint-disable-line no-magic-numbers

    if (selectedTour) {
      let bounds = new mapboxgl.LngLatBounds();
      map.markers.visible.map(marker => bounds.extend(marker.coordinates));
      boundsArray = [bounds.getSouthWest().toArray(), bounds.getNorthEast().toArray()];
      fitBoundsOptions.padding = 150;
    }
    return (
      <div>
        <MapBox
          style={mapBoxConfig.style}
          // required here to load before MapBox rendering
          containerStyle={{ position: 'fixed', top: 0, left: 0, bottom: 0, right: 0 }}
          dragRotate={false}
          onClick={clearPoiMarkerSelection}
          fitBounds={boundsArray}
          fitBoundsOptions={fitBoundsOptions}
          ...
```
