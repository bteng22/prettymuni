# To-Do

# essentials
- [x] base maps
- [x] get and parse muni data
- [x] draw muni vehicles for a given route
- [x] update every 15 seconds
- [x] transitions for vehicle updates
- [x] map zoom and pan
- [x] handle resizing of window
- [x] figure out how to add at any zoom level
- [x] route text labels for vehicle circles
- [x] better method for animating for route label and vehicle circle
- [x] click data for vehicles
- [] add promises so that vehicles aren't drawn until after basemaps.
- [] draw route paths
- [] hover data for vehicles
- [] simple loader
- [] allow selection of subset of vehicles for display from HTML5 control
- [] clear selections + visible button
- [] a decent base color pallete

# nice-to-haves
- [] vehicle headings
- [] a neat vehicle svg
- [] show all button

# bugs
- [x] when a new vehicle is added (or removed?) from a route, the route is being shuffled.  perhaps the order of the vehicles is not guaranteed and i should sort by id.  fixed by passing second parameter to .data() so it can keep track
- [] handle cases of predictable:'false' -- getting stranded circles right now.
- [] when dropdown is open, it cannot be closed without clicking in the top container area.  a click on the map should definitely close it too.


# bandwidth and performance observations
- 1.1kb per route
- ~80kb to get all routes
- streets geoJSON is 9mb and probably needs to be simplified
- 530kb .js
- 20kb css
- 48kb font
- miserable performance with all routes on MS edge
- perf rankings:  chrome, firefox, edge.

# wow-zone
- [] use an elevation service to do a sweet altitude vis 
    https://developers.google.com/maps/documentation/elevation/start 
