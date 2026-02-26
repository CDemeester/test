---
name: Standard QSP task
about: A standard template for tasks to be executed by the QSP team.
title: "[QSP <proj>]"
labels: monday
assignees: ''

---

# Title of the work
## Background 
### Purpose 
Describe here the rationale for the work, what is the development for 
### Approach 
- Describe high level approach / main assumptions: anticipated solution. 
- *This should be filled before starting* 

## Implementation 
- Describe here what you did to implement. 
- List relevant biology, preclinical and clinical evidence etc needed to rationalize modeling choices.
- If needed for the discussion with peers, you should add math 
- You should provide screenshots and details for implementation in PKSim MoBi, allowing others to repoduce / repeat that implementation  
- Add screenshots
- Reuse the issue docuentation for the module documentation! (This is not lost work)   

## Simulation 
Describe how the simulation is composed, if any parameters were changed wrt modules. 

## Results and Discussion
- Describe the result of a run of the model with the implemented feature of revision and discuss implications. 
- For bigger chunks of work, compare with available data. 
- Include figures, screenshots and tables as you see fit, link to any markdown / quarto document
 
## ToDo
- What needs still to be done to close that does not merit a sub issue or standalone issue 

## Dependencies and relationships 
- List here other issues / milestones / projects that are directly related to this issue 
- tag (cc @) people here 
- see here for example [[#8](https://github.com/esqLABS/QSP-T-qAOP-model-library-and-toolbox/issues/8)]

## Additional Files  
- Place here links to other relevant files (docs, data, pptxs, zipped pkmls, code, project files) which do not fit into the model library repo and which hekp / are needed for reproduction of the work described here

##  Checklist 
- [ ]  Issue filled so that other people can understand what you did  and why? 
- [ ] Are development /  implementation, results (of tests or comparison against data) dcumented (updated) here ? 
- [ ] Is there a model file / code part of the commit tied to this issue / PR or at least attached ? 
Thank you - you are done -> Close / Merge
