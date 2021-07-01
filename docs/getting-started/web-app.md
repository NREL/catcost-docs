# Getting Started: Web App

### Launching the web app

From the CatCost homepage, click "Web App" or go to https://catcost.chemcatbio.org/catalyst-estimate

You will land on the catalyst estimate list. When you arrive here for the first time, you will not have any estimates in your library. The web app allows you to create [multiple estimates](#multiple-estimates).

TODO: image of blank estimate list

### Loading the CatCost libraries

CatCost uses libraries to store input information about raw materials (Materials Library), catalyst production equipment (Equipment Library), and spent catalyst info (Spent Catalyst Library). You can access each library to add, remove, edit, or duplicate library entries using the links at the top of the screen.

TODO: image of libraries

To get started with the CatCost web app, you will ordinarily want to load the default libraries by clicking the orange "Add CatCost Default Materials, Equipment, and Spent Catalyst Libraries" button. You can also navigate to each library page individually and either load the default library (using the orange button) or upload your own file using the [File menu](#The-File-menu).

### The File menu

Every section of the CatCost web app has a File menu allowing you to import/export data in [JSON](https://www.json.org/json-en.html) format. This allows you to back up data and share with colleagues.

Options for the File menu, depending on context:

| Location within CatCost web app | Available options |
| --- | --- |
| Catalyst Estimate list | Open, Download, Delete All Estimates |
| Editing an estimate | Download |
| Materials Library | Open, Download, Clear Library |
| Equipment Library | Open, Download, Clear Library |
| Spent Catalyst Library | Open, Download, Clear Library |

Use "Open" to load a file from your computer into the web app, and "Download" to save information from the web app to your computer. Only the correct file type (estimate, materials-library, equipment-library, or spent-catalyst-library) can be loaded; if you have trouble uploading, please check you are in the appropriate File menu.

When downloading from the editing screen for a catalyst estimate, only that estimate will be downloaded. When downloading from the Catalyst Estimate list or one of the libraries, all of the entries from that list will be downloaded.

TODO: gif of a file being loaded into the web app

### Creating an estimate

To create an estimate, first ensure you have either loaded the [default CatCost libraries](#loading-the-catcost-libraries) or uploaded your own data.

Click on the + icon next to Catalyst Estimates to create your first estimate.

### Overview of estimate modules

In CatCost, a catalyst cost estimate is broken down into modules that are designed to be completed in order. The first two modules are  1 Inputs, for [global inputs](/estimation-methods/global-inputs) and 2 Materials, for [raw materials](/estimation-methods/raw-materials). For processing costs (all of the non-materials components of catalyst cost, such as equipment and labor costs), CatCost contains two [distinct methods](/estimation-methods/processing-cost-methods). In v1.1.0 of the web app, only the CapEx and OpEx Factors method is included. The [CapEx and OpEx Factors](/estimation-methods/capex-and-opex-factors) method uses modules 3b Equipment, 3c Utilities, 3d CapEx, and 3d OpEx. This concludes the estimation of purchase cost components, but it is critical for many catalysts to also consider the end-of-life value/cost of [spent catalyst](/estimation-methods/spent-catalyst), which is included in 4 Spent Catalyst. Finally, the cost outputs can be viewed using 5a Summary Outputs, 5b Detailed Outputs _(web-only in v1.1.0)_, or 5c Printable Outputs _(spreadsheet-only in v1.1.0)_

### Inputs and colors

#### Completion checks

<iframe width="560" height="315" src="https://www.youtube.com/embed/depIWmDr3L4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Important notes for the web app

#### Multiple estimates

The web app version of CatCost can contain multiple estimates. These estimates can share entries from the Materials, Equipment, and Spent Catalyst Libraries. For this reason, use caution when editing library entries, as it may change inputs for your other estimates. You can always duplicate a library entry and give it a different name if you want it to have different values for different estimates.

#### Data stored in browser

The web app runs locally in your browser. It stores all your content (estimates and libraries) in the browser you use to generate it. While your browser will check the CatCost website for an updated version of the tool each time it is run, <strong>no user-entered information, proprietary or otherwise, is transmitted to or stored on CatCost/ChemCatBio web servers.</strong> This also means that in order to retrieve previously entered estimates or library entries, you must open the same browser on the same computer that you used to build them, or download the info as a JSON file. We recommend backing up your estimates and libraries using the [File menu](#The-File-menu).
