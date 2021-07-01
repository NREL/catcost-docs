# Getting Started: Excel Spreadsheet

### Downloading

Download the latest CatCost Excel spreadsheet version from https://catcost.chemcatbio.org/downloads. You can also access past versions at https://datahub.chemcatbio.org/project/catcost-spreadsheet.

### Creating an estimate

In the Excel version of CatCost, each file contains one estimate. After downloading CatCost, we recommend making a new copy each time you want to start a new estimate. However, you may find it useful to customize the Excel spreadsheet with your own entries in the Materials, Equipment, and Spent Catalyst libraries, as well as by making changes to cost inputs such as the labor rate.

### Overview of modules

In CatCost, a catalyst cost estimate is broken down into modules that are designed to be completed in order. In the spreadsheet version of CatCost, the modules are worksheets within the overall CatCost workbook.

TODO: image of modules

The first two modules are  1 Inputs, for [global inputs](/estimation-methods/global-inputs) and 2 Materials, for [raw materials](/estimation-methods/raw-materials). For processing costs (all of the non-materials components of catalyst cost, such as equipment and labor costs), CatCost contains two [distinct methods](/estimation-methods/processing-cost-methods). In v1.1.0 of the web app, only the CapEx and OpEx Factors method is included. The [CapEx and OpEx Factors](/estimation-methods/capex-and-opex-factors) method uses modules 3b Equipment, 3c Utilities, 3d CapEx, and 3d OpEx. This concludes the estimation of purchase cost components, but it is critical for many catalysts to also consider the end-of-life value/cost of [spent catalyst](/estimation-methods/spent-catalyst), which is included in 4 Spent Catalyst. Finally, the cost outputs can be viewed using 5a Summary Outputs, 5b Detailed Outputs _(web-only in v1.1.0)_, or 5c Printable Outputs _(spreadsheet-only in v1.1.0)_

**Table 1.** Components of a catalyst cost estimate included in CatCost.

| **Module Name** | **Components of Catalyst Cost Analysis** |
| --------------- | -----------------------------------------|
| 1 Inputs | Global Inputs (Estimate Name, Basis Year, Output Mass Unit)Processing Cost Estimation Inputs (synthesis scale, margins, etc.) |
| 2 Materials | Yield and StoichiometryRaw Material Selection and PricingMaterial Losses During Handling |
| 3a Step Method_(Excel-only in v1.1.0)_ | Selection of Synthesis Steps with Costs in $/hrCalculation of Overall Synthesis Campaign CostProcess Templates for Common Catalyst Types |
| 3b Equipment(CapEx &amp; OpEx Factors Method) | Equipment List Including Sizes and Materials of ConstructionScaling of Equipment from Reference Scale to Estimate ScalePurchased Cost, Installed Cost, and Labor Factor for EquipmentProcess Templates for Common Catalyst Types |
| 3c Utilities(CapEx &amp; OpEx Factors Method) | Process Utilities Consumption and Unit CostsProcess Templates for Common Catalyst Types |
| 3d CapEx(CapEx &amp; OpEx Factors Method) | Factored Costs for Capital Expenditures:
- Direct Costs (piping, buildings, land, etc.)
- Indirect Costs (engineering, construction, contingency)
- Working Capital
 |
| 3e OpEx(CapEx &amp; OpEx Factors Method) | Factored Costs for Operating Expenditures:
- Direct Costs (labor, supervision, maintenance, supplies)
- Indirect Costs (taxes, insurance, rent, overhead)
- General Expenses (R&amp;D, distribution, administration)
 |
| 4 Spent Catalyst | Complete Treatment of the Value/Cost of Metals Recovery, Sale, or Disposal for Spent Catalysts:
- Metal and Support Attrition During Catalyst Use (using data on specific metals, supports, and reactor configurations)
- Value of Metals Content Including Spot Price Library
- Metals Recovery and Refining Fees
- Sale Values, where applicable
- Landfill Costs for Different Hazard Classes
 |
| 5 Outputs | Complete Catalyst Cost via Step MethodComplete Catalyst Cost via CapEx &amp; OpEx FactorsCombined Catalyst Cost Using Both Methods in a Mix and Match Approach |
| Libraries_(bundled information to facilitate estimates; user-expandable)_ | Materials Library, Step Library, Equipment Library, Spent Catalyst Library, Automated Unit Conversions (UnitConv), US Bureau of Labor Statistics Chemical Producer Price Index (ChemPPI), _Chemical Engineering_ Plant Cost Index (CEPCI) |

### 

### Inputs and colors
### Basic inputs
### How much detail here????

<iframe width="560" height="315" src="https://www.youtube.com/embed/depIWmDr3L4" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
