# hicues

`hicues` (**HI**ndenburg **CUES**) is a command line helper tool for [Hindenburg Journalist](https://hindenburg.com/products/hindenburg-journalist) that reads a project file and lists the cue points and their locations on the timeline along with their names. [As of October 2021](https://web.archive.org/web/20201021210138/http://support.hindenburg.com/forums/224350-general/suggestions/33099493-view-cue-points), you cannot get such a list within Hindenburg Journalist itself.

![Example output](https://gitcdn.link/repo/andrashann/hicues/master/hicues.png)


By default, the program keeps running and listens to changes to the file; the output is refreshed when the file is changed.

## Installation

The best way to install hicues is via pip: `pip install hicues`. You can alternatively install it from the source: `python setup.py install`.

## Usage

### Basic usage

Run the program in the command line using `hicues path/to/myproject.nhsx`. You will then see a table with the cue points in your project (if there are any). The table gets refreshed when you save the file. You can stop the program by pressing `ctrl-c`.

### Command line parameters

For more advanced use cases, you can use some of the following parameters.

<table>
<thead>
  <tr>
    <th>flag</th>
    <th>option</th>
    <th>description</th>
  </tr>
</thead>
<tbody>
  <tr>
    <td>-h</td>
    <td>--help</td>
    <td>Show the help</td>
  </tr>
  <tr>
    <td>-t</td>
    <td>--no-track</td>
    <td>Don't show track names in the table-formatted output</td>
  </tr>
  <tr>
    <td>-r</td>
    <td>--no-region</td>
    <td>Don't show region names in the table-formatted output</td>
  </tr>
  <tr>
    <td>-d</td>
    <td>--dump</td>
    <td>Dump the list of cuepoints to output once instead of watching for changes forever</td>
  </tr>
  </tr>
    <tr>
    <td>-v</td>
    <td>--verbose</td>
    <td>Print diagnostic messages to stderr</td>
  </tr>
  <tr>
    <td>-j</td>
    <td>--json</td>
    <td>Output the results in JSON format instead of a formatted table</td>
  </tr>
  <tr>
    <td>&nbsp;</td>
    <td>--json-indent</td>
    <td>If the output is JSON, this many spaces will be used to indent it. If not passed, everything will be on one line</td>
  </tr>
</tbody>
</table>

### Python package

The main function, `get_cue_points_from_file()` can be accessed by

```python
from hicues import cue_finder
cue_finder.get_cue_points_from_file(filename)
```

This function returns a dictionary with the cue points ordered by their appearance on the timeline. Each cue point has four keys: `timestamp`, which is a `datetime.time` object with the location of the cue point on the timeline; `name`, the label associated with the cue point; `region`, the name of the region to which the cue point is attached; and `track`, showing the name of the track where the the region is located.

## Contributing

Issue submissions and pull requests are welcome. Simple fixes do not require an issue to be submitted, however, do submit one if your pull request includes a lot of changes or new features.

## Changelog

- 0.1.0:
    - initial public release
