# GLAM Workbench Data Repository Template

This template repository contains some useful scripts for updating RO-Crate metadata files and Frictionless table schemas.

It's assumed that the datasets in this repository will have been generated using a GLAM Workbench code repository. You can use the `update_crate.py` script in the code repo to generate a `ro-crate-metadata.json` file for this repository.

The RO-Crate file for a data repo differs from the version created for a code repo. In particular:

- ids for notebooks are converted to full urls pointing to the code repo
- ids for datasets are converted from full urls to file names
- only notebooks that generate data files are included

The `update_data_crate.py` script in this template updates file details and versions in the `ro-crate-metadata.json` file, and also generates and links a Frictionless Table Data schema file.

The basic steps to creating a new data repository are:

- use this template to create a new GitHub repository
- copy the url of the new repository
- in the code repository, run the `update_crate.py` script with the `--data-repo` parameter set to the url of the new data repo
- copy the datasets and the `ro-crate-metadata.json` file to the new data repository
- in the data repository run `update_data_crate.py` file to generate and link Frictionless Table Data schemas for each dataset
- edit the schema file to add names and descriptions to the column values
- generate a new README file from the `ro-crate-metadata.json` file by running the `generate_readme.py` script

To create a new version:

- use the `--version` option with `update_data_crate.py` to set a version number, eg: `v1.0`

To update existing datasets:

- copy the new versions into this repository and run `update_data_crate.py` to update dates and stats
- the script checks the updated datasets against the existing schemas, if columns have been added or removed, this validation will fail, in this case delete the schema file and run again

To add new datasets:

 - follow the steps under create a new data repo to generate a new `ro-crate-metadata.json` file
