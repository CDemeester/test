# esqlabsR project template (development version)

## Version 5.5.0

### Major changes

- Update {esqlabsR} to version 5.5.0
- Updated extension module "Species Extrapolation Module". To scale from human 
to any species, it is sufficient to create an individual of the respective species, 
and load the module "Species Scaling from Humans" that define parameters missing in other species.
- Add a template Organism structure 'Template_organism_BB.pkml', containing all organs (but not their sub-compartments), as spatial structures BB as pkml. Typical use case is to create a module that adds new containers to all standard organs.
- Add a template Organism structure 'Template_organism_BB_with_subcomparments.pkml', containing all organs and their subcompartments, as spatial structures BB as pkml.


### Minor improvements and bug fixes

- Add details on sharepoint project location and environment variable setup
- Add instructions on how to  use configuration snapshot workflow
- Add clarification on when to snapshot/restore project config
- Improved technical writing


## Version 5.4.0


### Breaking changes

- Removed legacy Excel configuration files (Applications.xlsx, Individuals.xlsx, ModelParameters.xlsx, Plots.xlsx, Populations.xlsx, Scenarios.xlsx)
- Removed old utility files and READMEs
- Removed legacy simulation files and ProjectConfiguration.xlsx
- Removed README.Rmd in favor of README.md

### Major changes

- `{esqlabsR}` version has been updated to 5.4.0
- Added `styler` package to renv for code formatting
- Updated renv to version 1.1.2
- Install osp package from release tags + update CRAN packages

### Minor improvements and bug fixes

- Project template contains the RStudio project file `.Rproj` (\#22)
- Enhanced collaboration instructions and setup (\#21)
- Safer renv initialization (\#27)
- Add instruction for restore/snapshot environment for users
- Add a .Rprofile script that will help the user initializing/setup its project environment (\#16)
- Add utilities-transfer-functions (\#18)
- Add packages to default config (\#12)
- Update script (\#7)


