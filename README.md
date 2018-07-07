## TODO


### Features

* [x] map via geojson.io
* [X] Preserve features on existing GJ features
* [X] Point geohash (`echo 12,34 | geoq gh point 4 => abcd`)
* [X] Geojson geom printing
* [X] Geojson feature printing
* [X] Geojson feature collection aggregation
* [X] Add wkt writing -- perhaps borrow from https://github.com/CanalTP/rust-wkt/tree/write-wkt ?
* [ ] Map large JSON with embedded copy of geojson.io web page
* [ ] `filter intersects`
* [ ] `filter within`
* [ ] `gh children`
* [ ] `gh neighbors`
* [ ] `wkt geomcollection`
* [ ] `wkt multi` (linestring/poly/point? figure out how to decide)

### Improvements

* [X] Try assert cli for testing CLI "type" command https://github.com/assert-rs/assert_cli
* [X] Add rust-geohash and generate point geohashes
* [X] test reader matching functions
* [ ] Refactor reading interface to produce an iter<results> (i.e. let reader methods return errors)
* [ ] Migrate Geojson and WKT output formats to trait
* [ ] Add strings in error messages so, e.g. bad inputs can be printed with error
* [ ] Investigate parallel iterator processing (rayon?)
* [ ] Try streaming serde for feature collections: https://github.com/serde-rs/json/issues/345
* [ ] Make error types support string messages (or just make them strings? add a lookup table?)
* [ ] Geohash require valid precision level (1 - 12)
* [ ] Print invalid geometries to stderr (or exit program?)
* [ ] Make "exit on invalid" configurable
* [ ] figure out streaming geojson feature collection output
* [ ] cross-platform `open` command for geojson map
* [ ] Migrate back to official rust-wkt crate

Entity refactoring
problem: currently conversion methods take ownership -- getting geometry or geojson rep consumes original input
Alternative: turn entities to structs with lazily-populated fields (or even eager...maybe perf doesnt matter)
Entity
- raw / original
- properties map
- geometry

...then other operations can borrow these fields
