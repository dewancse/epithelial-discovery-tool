### Epithelial Modelling Platform (EPM)
Epithelial modelling platform is a web-based epithelial transport discovery, exploration and assembly tool. It allows users to discover, explore and assemble computational models for investigating their experimental or clinical hypotheses. In particular, this platform will aid biologists and clinicians to test their clinical or experimental hypotheses for a given collection of disparate mechanisms and/or observations such as diseases, drug actions and clinical observations.

### Installing EPM
Please do the following steps to clone the EPM in your workspace:

- git clone https://github.com/dewancse/epithelial-modelling-platform.git
- run the "server.js" with this command: "node ./src/js/server.js"
- open "index.html" in the browser
- install "CORS Toggle" to deal with cross browser origin issue.
- if you change something in any js files of the project, you need to execute webpack with this command: "webpack --progress --profile" 

### EPM workflow

#### Discover CellML Models
Presented below screenshot is an example of discovered models from the annotated information in the Physiome Model Repository (PMR) for a search term `flux of sodium`. From this, user can analyse CellML model entity which consists of name of the model, component name and variable name; biological annotation deposited in PMR; protein name; and species and genes used during the experiments. We have provided two options for further investigation: 
- `View Model` to explore more information for a specific model 
- `Add to Model` to include a list of models to be considered for next round.

However, user can come back and rediscover more models in this `MODEL DISCOVERY` page.

#### Input requirements
We have maintained a dictionary as name and value pairs to map searched text with URIs, without applying Natural Language Processing technique. However, this would be integrated later to make this process dynamic.

Therefore, mapping follows `exact match` principle. It is case insenstitive and users have to include the following terms when searching for a model:

| Physical entity | Physical process | Solutes |
| --- | --- | --- |
| `concentration` | `flux` | sodium, hydrogen, chloride, potassium, ammonium |

<center><img src=src/img/modeldiscovery-main.png /></center>

#### Load Discovered Models
After discovering a range of models, user will select some models of interests and store these into a separate list, as presented below in the screenshoot. In this case, we have provided the following options: 
- `view` to get more information of a seleted model
- `delete` to delete model(s) if user is not happy with that list
- `visualisation` to get a comparison between models
- `Epithelial Platform` option to visualize the selected models as SVG in the epithelial platform.

<center><img src=src/img/loadmodel-main.png /></center>

#### Model Similarity
Using this feature, user can easily find similar component between models. As can be seen in the screenshot below, weinstein and mackenzie models have common `compartment`.

<center><img src=src/img/modelsimilarity-main.png /></center>

#### Modelling Platform
This platform has been generated from the discovered models in the `LOAD MODELS` page. Following screenshoot illustrates semantically generated models’ component as circles, polygons and line with arrows. It has two membranes: apical and basolateral; and four compartments: luminal, cytosol, interstitial fluid and paracellular pathway. Each of this has been depicted with a unique color on the top right corner of the platform.

Concentrations will be floating around on a specific compartment and the fluxes will be placed on a specific membrane based on the annotation in PMR. For example, Na+ and Cl- are floating from luminal to cytosol compartment across apical membrane and NaCl cotransporter in the presented below screenshot. In order to make distinction, we have represented physical entities and processes with specific shapes:
- `single fluxes` and cotransporters with `circles`
- `channels` with `polygons`
- `diffusive fluxes` in the paracellular pathway with a `text` and an `arrow`. 

On the right, we have generated checkboxes for each of these representations. User can drag and drop fluxes across membranes. For example, user can drag and drop the NaCl cotransporeter, shown in the screenshot, on the basolateral membrane in order to get some useful suggestion which is discussed below in the `Recommender System` section.

<center><img src=src/img/epithelial-main.png /></center>

#### Recommender System
This system will appear as a window when user will drag and drop a model across the apical or basolateral membrane. Presented below is an example of a CellML model entity - `flux of sodium` in the weinstein model after dragging from apical to basolateral membrane. Initially this system gives a brief description of the dragged model followed by some suggestions from the annotation in PMR. By using this system, user will get existing basolateral membranes with the sodium solute. Also, alternative models of this model from various workspaces, and related kidney models have been provided for further exploration. User can choose one of the models from this system as a replacement of the dragged model.

<center><img src=src/img/recommender-main.png /></center>

### Accessibility
The application is accessible by navigating::
```
  https://dewancse.github.io/epithelial-modelling-platform/src/index.html
```

### Quality control
We have testing in place to make sure the code is functioning as expected (TODOs). In addition, the code allows reproducibility and reuse of modules (TODOs). 

### Programming Language
- JavaScript
- SPARQL

### Limitations
Need to solve the TODOs under the `Quality control` section.

### List of contributors
- Dewan Sarwar
- Tommy Yu
- David Nickerson

### Licencing
MIT license!

### Acknowledgements
This project is supported by the MedTech Centre of Research Excellence (MedTech CoRE) and the Auckland Bioengineering Institute.