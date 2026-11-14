# Interplanetary Survival Guide: Martian Map

A browser map of Mars that layers several NASA datasets and walks through the first leg of Curiosity's route, from its landing site toward Mount Sharp in Gale Crater. It was built for the 2026 NASA Space Apps Challenge, "Interplanetary Survival Guide: Martian Map", which asks for a layered view of a Martian location or route that a human explorer could use to plan a Marswalk.

## Running it

Open `index.html` in a current browser. There is no build step and nothing to install. The page loads Leaflet and the Mars tiles over the internet, so it needs a connection.

To serve it locally instead, run `python3 -m http.server` in the project folder and open `http://localhost:8000`.

## What it does

The basemap is the Viking color mosaic. Four overlays can be switched on from the layers box: MOLA elevation, THEMIS daytime infrared, a high-resolution MRO Context Camera mosaic of Gale Crater, and USGS geologic units. Geologic units load only at zoom 6 or closer. A legend appears while the elevation layer is on, and a notice appears if a layer's tiles fail to load.

Six sites can be reached from a dropdown or from map markers: Jezero Crater, Olympus Mons, Valles Marineris, Gale Crater, Bradbury Landing and Hellas Planitia. Each popup gives a figure and links to its NASA source.

Mission mode steps through four stops: Bradbury Landing, Yellowknife Bay, Pahrump Hills and Murray Buttes. Each stop shows a short description, its coordinates, the straight-line distance and walking time from the previous stop, a source link, and a link to a photo taken by the rover.

The route planner lets you click points on the map, or on site markers, to build a multi-leg route. It reports total distance in kilometers and miles and the walking time at the pace you enter, which defaults to 2 km/h. Distance is calculated with the haversine formula on Mars' mean radius of 3,389.5 km.

A radiation reference card in mission mode summarizes Curiosity's RAD measurements. The instrument recorded an average of about 0.67 mSv/day from galactic cosmic rays on the surface (August 2012 to June 2013) and about 1.8 mSv/day in transit. Round-trip transit adds about 0.66 Sv and 500 days on the surface adds about 0.34 Sv, which gives a total near 1 Sv. This is a reference figure and not a map layer.

## Data sources

Imagery and elevation come from NASA Mars Trek (https://trek.nasa.gov/mars/):

- Viking MDIM 2.1 Color Mosaic, 232 m/px, NASA / JPL / USGS.
- Mars Global Surveyor MOLA colorized shaded relief, 463 m/px, NASA. The colors are qualitative and show relative height.
- Mars Odyssey THEMIS daytime infrared controlled mosaic, 100 m/px, NASA / ASU. It shows infrared brightness and is not a temperature map.
- MRO Context Camera mosaic of Gale Crater, about 5 m/px, NASA / JPL / Malin Space Science Systems.

Geologic units come from Tanaka et al. (2014), [Geologic Map of Mars, USGS SIM 3292](https://pubs.usgs.gov/sim/3292), at 1:20,000,000, served by the USGS Astrogeology Science Center on ArcGIS.

Mission stop positions were read from the NASA/JPL Curiosity traverse map [PIA21144](https://photojournal.jpl.nasa.gov/catalog/PIA21144). Stop descriptions and photo links:

- Bradbury Landing: [PIA16768](https://photojournal.jpl.nasa.gov/catalog/PIA16768)
- Yellowknife Bay: [NASA/JPL on the first Mars age measurement](https://www.jpl.nasa.gov/news/nasa-curiosity-first-mars-age-measurement-and-human-exploration-help) and [Mastcam panorama](https://science.nasa.gov/photojournal/view-from-inside-yellowknife-bay/)
- Pahrump Hills: [NASA/JPL on the first drill sample from Mount Sharp](https://www.jpl.nasa.gov/news/nasa-rover-drill-pulls-first-taste-from-mars-mountain/) and [PIA18608](https://photojournal.jpl.nasa.gov/catalog/PIA18608)
- Murray Buttes: [PIA18392, traverse over the first 663 sols](https://www.jpl.nasa.gov/images/pia18392-curiosity-rovers-traverse-first-663-sols-on-mars/) and [Mastcam panorama](https://science.nasa.gov/photojournal/rovers-panorama-taken-amid-murray-buttes-on-mars/)

Site figures:

- Olympus Mons and Valles Marineris: [NASA Science, Mars Facts](https://science.nasa.gov/mars/facts/)
- Jezero Crater: [NASA, Perseverance deciphers the ancient history of a Martian lake](https://www.nasa.gov/missions/mars-2020-perseverance/perseverance-rover/nasas-perseverance-rover-deciphers-ancient-history-of-martian-lake)
- Gale Crater: [NASA/JPL, Mount Sharp inside Gale Crater](https://science.nasa.gov/resource/mount-sharp-inside-gale-crater-mars/)
- Bradbury Landing: [NASA, Destination Gale Crater in August 2012](https://www.nasa.gov/image-article/destination-gale-crater-august-2012)
- Hellas Planitia: [NASA/JPL, HiRISE "To Great Depths" (PIA21570)](https://science.nasa.gov/photojournal/to-great-depths)

Radiation figures: [SwRI press release on Hassler et al., Science (2013)](https://www.swri.org/press-release/swri-scientists-publish-first-radiation-measurements-surface-mars).

## Third-party software

The only library is [Leaflet](https://leafletjs.com) 1.9.4, licensed BSD-2-Clause and loaded from cdnjs. The map data above comes from NASA and USGS services and is credited in the app's "Data and credits" panel.

## Limitations

- Legs between mission stops are straight lines, not the rover's path. From Yellowknife Bay to Pahrump Hills the rover drove more than 8 km, which is much longer than the line drawn on the map.
- Stop positions were read from a labeled map and are accurate to within a few hundred meters.
- There is no slope or elevation profile along routes, no rock or hazard map, and no live space-weather data. Routes do not avoid obstacles.
- The walking pace is an adjustable assumption and not a NASA figure. Suit mobility, slopes and rocks would slow a real crew.
- The geologic units are mapped at 1:20,000,000. They give regional context and are not reliable at walking scale.
- Clicking the map gives coordinates only. The layers are rendered images, so exact elevation at a point is not available.
- The boxwork formations that Curiosity studied in 2025 are the stated goal of the mission but are not mapped here.
- The app depends on external services (NASA Mars Trek, USGS on ArcGIS, and the Leaflet CDN) and will not work offline.


