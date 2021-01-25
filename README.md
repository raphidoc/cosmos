# cosmos

COSMOS intend to be a Common Organized Structure for Multiple Objects Sharing. This git repository is used to develop the specifications and standards we want to use at Aquatel lab, it's a place of dialog to define best practices in our field of expertise.

Our most high level of granularity is the `project`. It's a wide entity defined by it's `space`/`time` and by the various kind of `methods` deployed to collect data. Different kind of observation require different kind of storage structure.
The goal of this project is to streamline and describe the data structure (from top level `project` folder to variables names), hence improving the sharing and discoverability of the data. 
To the end of improving the discoverability of the data we should consider implementing a [STAC](https://github.com/radiantearth/stac-spec) catalog linking individual items in database(s).

Specifications described here will be enforced with the lighthouse package, so one requirement is to define them in a way that will not be subject to backward compatibility issue for as long as possible (trade off between generality and specificity) (See [Versioning](#Versioning)).

# Organisation of the repository

Every concepts and descriptions can be found in (or from) this repository.

- Overview give a global sense of the proposed folder structure.
- Folder /set-spec contains every defined specification for a given `set` and associated real world example.
- Folder /data-dic contains the definition off every elements to be found in the /folder-structure as well as in the /database.

# Contribution

To contribute to this project, you can fork the repository and make `merge request`. Additionally you can ask to be granted permission to create new branch and work directly from here.
Contribution can also take the form of creating an `issue` when you find a problem, an incoherence, think of an improvement or whant a specific feature to be added.

# Branch specification

The `main` branch intend to be stable at all time, to propose a modification, contributors must create separate branch where they can work freely. Once they think their work is complete, they can propose a `merge request`. During the merge request, the proposed change are reviewed and discussed, further modification can be requiered an performed.
This approach ensure a consistent way of collaborating and documenting the developement process while it is happening.

# <a name="Versioning"></a> Versioning

This project uses [semantic versioning](https://semver.org/). During initial development phase everything can be subject to changes, once it reach version 1.0.0 incompatible change will need to go to 2.0.0.