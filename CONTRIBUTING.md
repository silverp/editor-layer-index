## Contributing

### Prerequisites
* Command line development tools (`make`, `git`) for your platform
  * Ubuntu: `sudo apt-get install build-essential git`
  * Mac OS X: Install Xcode and run `xcode-select --install` from a command line
* Python and Pip
  * Ubuntu: `sudo apt-get install python-pip python-dev`
  * Mac OS X (via [Homebrew](http://brew.sh/)): `brew install python`, then `brew linkapps python`
* `jsonschema` package (for running `make check`)
  * `pip install jsonschema`

### Adding new sources
The 'source' documents for this project are the .json files in `sources`. To add
a new imagery source, add a new file to this directory.

##### Dates
Specifying reduced accuracy dates is complex. For simplicity, the schema allows
a subset of ISO 8601 defined in [RFC 3339](http://tools.ietf.org/html/rfc3339#section-5.6)
except that a reduced precision date is allowed. For example, `2013-04-15T14:02:54.05+00:00`
is a fully specified ISO 8601 date-time, `2013-04-15` could be used for just the date,
or `2013-04` for just the month, `2013` for just the year.

Implementations may round down the end date (e.g. consider `2013` the same as the
start of `2013` so to specify imagery taken sometime in 2013, use `"start_date": "2013"`,
`"end_date": "2014"`.

### Building the combined files

After you've made a modification:

1. run `make check` to validate the source files against `schema.json`
2. run `make` to generate `imagery.xml`, `imagery.json`, and `imagery.geojson`
