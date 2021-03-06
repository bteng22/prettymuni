# https://www.prettymuni.com
 
Uses D3.js and vanilla javascript to show and update current positions of realtime buses in the San Francisco Muni system.

Read about the process at https://medium.com/@jamesbpollack/pretty-muni-71773427e83d

![Alt text](https://github.com/imgntn/prettymuni/raw/master/screenshot.PNG?raw=true "Optional Title")

# Running the project
Everything is in the /docs folder so that Github Pages will serve it.   

`npm install`

`node devServer.js`

Then visit http://localhost:3000

You'll want to swap out the https proxy url link in the Mapper.js and the Github pages links in index.html for your own, once you're ready to deploy.

One big object literal in Mapper.js so things are easy to read.

No frameworks because that's a lot of extra javascript to deliver and parse before we even start with our app, and we're already facing large sizes with the map JSON.

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
- [x] allow selection of subset of vehicles for display from HTML5 control
- [x] remove unused routes on select
- [x] clear all button
- [x] vehicle headings
- [x] dictionary of colors for routes so that new vehicles come in with the same one their route already has.
- [x] route selection list:  full screen, show route tag, touch tile to toggle, fill the active routes list
- [x] simple loader

# nice-to-haves
- [x] active color of tile is bus route color
- [x] teardrop heading indicator
- [x] load street map async 
- [x] fade in the streets when they are loaded async so that it looks nice
- [x] show route name  in route selector tile at larger sizes
- [x] draw route paths
- [x] send google analytics event on route toggle
- [] add button press down states
- [] scale vehicle groups down as you zoom in so the fit the streets.
- [] custom, thematic loader.  
- [] offline detection 
- [] add gulp deploy task for copying a /public folder into /docs to cleanup that naming mess and detach github pages pushes from production
- [] favorite routes
- [] favorite colors
- [] manifest to install as home screen app
- [] animate route paths
- [] pre filter routes with no vehicles out of route selector
- [] vehicle location transitions could be projected along the vehicle paths.
- [] button down states

# bugs
- [x] when a new vehicle is added or removed from a route, the route is being shuffled. fixed by passing second parameter to .data() to keep track
- [x] handle cases of predictable:'false' -- getting stranded circles right now.
- [x] when dropdown is open, it cannot be closed without clicking in the top container area.  a click on the map should definitely close it too.
- [x] mouseover brings group to front of route.  needs to bring route to front of other routes also.
- [x] mixed content warnings since the nextbus api isn't https. fixed by creating my own proxy
- [x] mobile: can't close dropdown at all :P even when pressing 'done' https://github.com/Dogfalo/materialize/issues/3501
- [x] browser default looks like crap on desktop and i don't want to start doing feature detection, so i think i'll roll my own.
- [x] remove material design, jquery
- [x] need my own route selector, layout, buttons. 
- [] rotations on tearpdrop transitions are weird.  redraw tear path SVG so it is around origin, or create a group and pre-translate and then attach the paths to that (rotate the group)

# bandwidth and performance observations
- 1.1kb per route from nextBus
- ~80kb to get all routes at once
- still 1.9mb to fetch all maps
- 107 kb javascript files
- 2kb css
- 11kb fonts
- perf rankings:  chrome, firefox, edge.
- MS edge perf is extra bad.
- a bit poky on the chromebook but it does run all routes.
- perf problems are likely related to the number of svg elements.  dom manipulation can get slow.
- should add caching so i'm not transforming / transitioning locations and headings that haven't really changed. this could be a filter/threshold 
- i could add passive event listeners to d3.js -- scrolling messes with the main thread
- doing the drop and dot as a group and then rotating that group around the other group containing the text and circle would reduce listeners.

#  someday
- [] use an elevation service to do a sweet altitude vis 
    https://developers.google.com/maps/documentation/elevation/start
- [] html5 geolocation + 'show nearest'
- [] maybe use topoJSON (what are expected savings?)
- [] maybe use vector tiles http://bl.ocks.org/mbostock/5616813 https://mapzen.com/projects/vector-tiles/
- [] every route line path has two inner lines for inbound outbound directional pulse wave along the stops
- [] generative audio


# physical objects
- [x] custom print a set of basemaps w/ selected routes at a specific date or time of day
