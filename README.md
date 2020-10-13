# Jake's Recipes
This project generates various ways to display Jake's recipes while tracking 
previous versions/releases.

## Accessing Recipes
How can you access these recipes? Good question! Here are three answers:

### [Website](https://jakeod99.github.io/recipes) - COMING SOON
You can visit this [website](https://jakeod99.github.io/recipes)! It is a very 
basic, static website hosted on Github Pages. It provides features other 
mediums can't, like generating shopping lists. It will always display the most 
recent release. To view older releases, opt for the markdown or document 
options available in the `versions` folder.

### Document - COMING SOON
Upon new releases, this system will generate a document (`.docx`) of each of 
Jake's recipes, intended to resemble a cookbook. This can be printed out, 
three hole punched, and inserted into a binder. That way you can physically 
provide people with these recipes instead of pointing them to an online 
resource. All versions (past and present) can be seen in the `versions` 
folder, but for quick access to the current version, see the `current` folder. 

### Markdown - COMING SOON
Upon new releases, this system will generate markdown copies of every one of 
Jake's recipes - both in unique files and as a part of one big compilation. 
All versions (past and present) can be seen in the `versions` folder, but for 
quick access to the current version, see the `current` folder. 

## Questions, Comments, and Suggestions
If you have any general questions/comments, or if you have any suggestions 
after perusing, please feel free to open an `issue` 
[here](https://github.com/jakeod99/recipes/issues). Jake will do his best to 
address what you bring up. If you see something in a recipe that seems wrong, 
it's probably a mistake! I would greatly appreciate you alerting me to the 
specific problem by opening an `issue`.

## Development

### <a name="gar"></a>Generating a Release
To generate a fresh release, run `release.js` in command line, like 
so: 
```cmd
cd ~/workspace/recipes/scripts
node release.js 0.1.0
```
Doing this should overwrite the contents of `current` and `docs`, as well 
as add a new entry into `version`. The release that this specific example 
would generate would be version `v0.1.0`. Generally speaking, the version 
digits represent the following increments `MajorRelease.StageVersion.Feature`. 

### Basic System Overview
Frankly, this is a bit homegrown and doesn't follow any traditional 
organizational structure. The system has five main sections: `content`, 
`current`, `docs`, `scripts`, and `versions`.

#### Content
This is where all the actual recipe information is stored. Everything is 
stored as `.json` and categorized as a `base` or a `recipe`. This is not the 
ideal format for viewing the recipes, it's merely how the system reads in the 
information it needs to generate a more pleasing user experience. That said, 
if you honestly want to view the information as straight `.json`, then who am 
I to stop you - it's a free country.

#### Current
This is a duplicate of the most recent version in the `versions` folder. It is 
here for quick access and so that a single unchanging link can always point to 
the most recent version. This means the naming scheme of the contents of this 
folder must be kept consistent, and therefore independent from their 
respective version.

#### Docs (Website)
This folder holds all of the frontend code to be rendered by Github Pages. 
A name like "website" would have been far clearer, but the Github Pages 
configuration options do not currently allow for a custom folder name as the 
site's base. Generating new releases will overwrite this folder without saving 
previous versions. This is the only display format which does not save 
previous versions, so if you desire older content please look in the 
`versions` folder and settle for the markdown or the cookbook document. The 
website can be seen hosted at https://jakeod99.github.io/recipes.

#### Scripts
This is where all the logic is kept. Running `release.js` should 
trigger all the necessary generations and overwrites housed here. To run 
`release.js`, see [Generating a Release](#gar).

#### Versions
Every version generated that updates recipe content and increments the 
`StageVersion` digit is stored here indefinitely. Of course, during 
development of a feature, feature branches will temporarily store featured 
versions (or versions which increment the `Feature` digit). When merging into 
the `stage` branch, be sure that these are scrubbed and that the newest 
version increments `StageVersion` (e.g., `v1.3.0` or `v2.0.0`, but not 
`v1.5.3`). 

### Tech Stack
It's basically just a bit of straight javascript that produces really basic 
markdown, documents, and HTML/CSS. No third party frameworks, just the 
breakdown that's described in this document. This does, however, use the 
[docx.js](https://docx.js.org/api/) library to generate the `.docx` cookbook. 

### Git Flow
All work flows from feature branches, into the `stage` branch for stage 
versions, and ultimately into the `master` branch for major releases.

#### Feature Branches
All development and content management should happen on feature branches. 
Feature branches are temporary, and are named according to the `StageVersion` 
they seek to introduce (e.g., `v1.5.0`). This means that the work done on a 
given feature branch `v1.3.0` would mostly be done with the `StageVersion` `2` 
(with development versions like `v1.2.2` and `v1.2.6`). The `v1.3.0` 
feature branch would conclude by generating `v1.3.0`, scrubbing all `v1.2.X` 
versions (with the obvious exception of `v1.2.0`), and merging into the 
`stage` branch. That said, if for whatever reason the changes being merged 
into `stage` do not necessitate generating a new version (logic changes, 
stylistic tweaks, etc.)

#### Stage Branch
The `stage` branch persists, and is where all feature branches flow into. When 
the system is ready for a new major release, the most up-to-date version on 
`stage` should be a major release (e.g., `v.1.0.0` or `v2.0.0`), and it should 
be pulled into `master`. No development should occur directly on `stage`, it 
is merely a holding place for stage versions, which ultimately culminate to a 
major release. 

#### Master Branch
The `master` branch persists, and is where all officially released material 
resides. The most up-to-date version on the `master` branch should always be a 
fresh major release (e.g., `v1.0.0` or `v2.0.0`). This is where all references 
to Jake's recipe work should point, whether it's showing the current major 
release or providing access to a deprecated recipe in the `versions` folder. 
Everything in other branches are still under development and subject to 
change. 

## Thanks!
Jake has spent a lot of time learning about cooking recently, and there are a 
lot of people he has to thank. Whether they provided recipes he worked from, 
or if they taught him general cooking tips, or if they patiently suffered 
through his frustrating perfectionist tendencies, he certainly has a lot of 
reason to be thankful for their help and guidance. They are:

- Audrey Moore
- Joanne O'Donnell
- Bart Chumbley
- [Adam Regusea](https://www.youtube.com/user/aragusea)
- [Andrew Rea](https://www.youtube.com/user/bgfilms)
- [John Mitzewich](https://www.youtube.com/user/foodwishes)