# ESQlabs Project Template

Welcome to your new ESQlabs project! This README will guide you through everything you need to know to get started. 📊

## 🚀 Quick Start Guide

### Initialize the project 

1. **Open the project in RStudio** by double-clicking the `.Rproj` file
2. Make sure that a **`GITHUB_PAT`** token is defined. See https://r.esqlabs.com/troubleshooting.html for documentation.
3. **Install required packages** by running in the R console:
   ```r
   renv::restore()
   ```
4. **Add your project description** at the top of this file

### Using {esqlabsR} Framework

If you are setting up the project structure, initialize the project. This step must be performed only once, usually by the project lead.

**To initialize the esqlabsR framework:**

1. Check if your project is already initialized by looking for `ProjectConfiguration.xlsx` in the project root.
2. If the file doesn't exist, initialize the project:
   ```r
   esqlabsR::initProject()
   ```

> ⚠️ **Important**: Only run this command once per project.

Learn more about the [esqlabsR project structure](https://esqlabs.github.io/esqlabsR/articles/esqlabsR-project-structure.html).

### Link observed data files located on SharePoint
Use SharePoint to collaborate on Excel data files (not the configuration files!).

1. Sync your project's SharePoint folder to your computer.
2. Move Excel data files from the `Data` folder to your SharePoint folder (to be done by project lead at the initialization of the project).
3. After loading the project in RStudio, open your project `.Renviron` file:
   ```r
   usethis::edit_r_environ(scope="project")
   ```
4. Add the SharePoint path:
   ```
   PROJECT_DATA_FOLDER="path/to/your/sharepoint/project_folder/data_folder"
   ```
5. In `ProjectConfiguration.xlsx`, set the `DataFolder` value to: `PROJECT_DATA_FOLDER`
6. Restart RStudio.

> ⚠️ **Important**: Use SharePoint only for data files. For project configuration files, use the snapshot method above.

## 📋 What's Included

This template comes with everything you need to start a standardized ESQlabs project:

- **Ready-to-use folder structure** for organizing your work
- **Pre-configured R environment** to ensure consistency across team members
- **Version control with Git** to track changes and collaborate effectively
- **PK-Sim models and modules** for pharmaceutical modeling tasks

## 📁 Project Organization

After initialization the project or checking out the repository with initialized project, your folder structure should look like this:

```
├── Code/     # Your R scripts and functions
├── Data/     # Raw and processed data files - must be moved to SharePoint!
├── Models/   # Model files (includes pre-built templates)
├── Reports/  # Documentation and reports
└── Results/  # Output files, plots, and analysis results
```

## 🧰 Essential Tools

### Package Management

This project uses `renv` to maintain consistent R package versions across your team.

**First-time setup:**

Install all required packages:
```r
renv::restore()
```

**To add new packages:**

1. Install the package:
   ```r
   renv::install("packageName")
   ```
2. Update the lock file:
   ```r
   renv::snapshot()
   ```
3. Commit the updated `renv.lock` file to Git.

**To sync with team updates:**

If you see this message:
```
- Project loaded. [renv]
- The project is out-of-sync -- use `renv::status()` for details.
```

Run this command:
```r
renv::restore()
```

## 🤝 Team Collaboration

### Collaborating on Configuration Files

Use configuration snapshots to share project settings with your team.

**To create and share a configuration snapshot:**

1. Create a snapshot of your project configuration:
   ```r
   esqlabsR::snapshotProjectConfiguration()
   ```
   This command creates or updates a JSON file with your project configuration settings.

2. Commit and push the snapshot to your Git repository.

3. **For team members:** Restore the configuration to match your settings:
   ```r
   esqlabsR::restoreProjectConfiguration()
   ```

**When to create snapshots:**
- After making significant configuration changes
- Before sharing new settings with your team
- When you want to save a working configuration

**When to restore snapshots:**
- To get the same configuration as your teammates
- To revert recent Excel file changes
- When setting up the project on a new machine

For more details, see the [esqlabsR documentation](https://esqlabs.github.io/esqlabsR/reference/snapshotProjectConfiguration.html).

### Working with Large Files

Git limits file sizes. Use Git LFS for files larger than 100 MB.

> 💡 **Note**: This template repository does not use Git LFS (since template repositories cannot include LFS files), but you can set up Git LFS in your project after creating it from this template.

**To add large files to your project:**

1. Install [Git LFS](https://git-lfs.github.com/) on your computer.
2. Initialize Git LFS in your repository:
   ```bash
   git lfs install
   ```
3. Track your large file:
   ```bash
   git lfs track "path/to/large/file.pkml"
   ```
4. Commit the file and tracking configuration:
   ```bash
   git add path/to/large/file.pkml
   git add .gitattributes
   git commit -m "Add large file"
   git push
   ```

## 📚 Pre-built Model Resources

### PK-Sim Project with Default Expression
Located at: `Models/Snapshots/Default_PBPK_Individual_V11_and_V12.json`

This file contains standard protein expressions used in DDI publications.

### Species Extrapolation Module
Located at: `Models/PKML/Module_Species_Scaling_from_Human.pkml`

This module helps with species extrapolations in MoBi from human to animal species.

Usage:
1. Start with a model using human spatial structure
2. Create an animal individual
3. Load the "Species Scaling from Humans" module
4. Add the individual and and the PV BB `Saliva_and_Gallbladder` from the extension module.

### Spatial Structure BB with Organism Template Structure
Located at:  `Models/PKML/Template_organism_BB.pkml`
             `Models/PKML/Template_organism_BB_with_subcomparments.pkml`

The pkml files add a template Organism structure containing all organs (w/wo sub-compartments), as Spatial Structure BB. A typical use case is to create a module that adds new containers to all standard organs or their subcompartments (see also TalentLMS course Lysosomal trapping M04-12).

Usage:
1. Create a new extension module 
2. Load the pkml as Building Block
3. Load that module after your base module


## 📘 Need More Help?

For Git and GitHub collaboration, see the [ESQlabs Git Guide](https://esqlabs.github.io/ESQlabs-r-guidelines/git_guide.html).

---
*Remember to replace this template content with your specific project information, but keep the instruction sections for reference.*
