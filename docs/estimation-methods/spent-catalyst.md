# Spent Catalyst Value: The _4 Spent Catalyst_ Module and _Spent Catalyst Library_

  1.
## Overview and _4 Spent Catalyst_ Module

While the procedures outlined so far for estimating materials and processing costs allow CatCost to provide a complete estimate of the initial purchase/synthesis cost of a catalyst at industrial scale, the initial cost of filling a catalytic reactor is only part of the story. Accurate comparisons of catalytic materials must consider the differing values of catalysts at the _end_ of their useful life. CatCost provides a Spent Catalyst Value module for this purpose, enabling comparisons between, for example, a molybdenum carbide catalyst with a relatively low purchase cost and a platinum-based catalyst with a high purchase cost but with significant spent catalyst value.

Within CatCost, the **4 Spent Catalyst** module estimates the value of three distinct options for spent catalysts: metals recovery, sale, and landfill. CatCost presents the value of each of the options and automatically chooses the most favorable option (i.e., if the cost to recover metal from a catalyst exceeds the value of the metal content to be recovered, CatCost first looks for sale value, and then finally chooses to landfill the catalyst if neither metals recovery nor sale were more favorable). Notably, CatCost presents the spent catalyst value as an individual line item in the catalyst cost outputs (Figure 9.1) so that the user can choose whether to include it in catalyst cost comparisons. This approach also allows the technoeconomic analysis-oriented user to enter the reactor filling and catalyst disposal inflows/costs at the appropriate times in a discounted cash-flow analysis of a catalytic process plant.

![](RackMultipart20210611-4-vy292y_html_322e4c74863745a3.jpg)

**Figure 9.1.** Excerpt from CatCost outputs showing the separate line item for Spent Catalyst Value.

The inputs to CatCost for the **4 Spent Catalyst** module are shown in Figure 9.2 below. These inputs, shared by the Excel and web versions of CatCost, allow the tool to look up values from the Spent Catalyst Library (described below) and to perform calculations. Built-in logic allows CatCost to determine the best-value option for the spent catalyst based on these inputs. For details of the logic being used, see the following sections. The first two inputs to **4 Spent Catalyst,** &quot;Metal to recover&quot; and &quot;Support,&quot; allow CatCost to estimate the attrition losses during catalyst use and metals refining, as well as to look up the appropriate spot metal price from the Spent Catalyst Library. The third input, &quot;Metal wt. % of AP&quot; (the weight fraction of the recoverable metal in the active phase; for example, for a Rh2P active phase this number is 86.92%), is used with the &quot;Active Phase Weight Percent&quot; field on **2 Materials** to determine the metal content in fresh catalyst. The fourth input, &quot;Catalyst Bulk Density,&quot; may be entered in units of either lb/ft3 or kg/m3 and is used in calculation of refiner &quot;incoming&quot; and &quot;metal contaminant&quot; fees (described below), both of which have a volumetric basis (e.g., $105/ft3). CatCost automatically converts the user-entered density according to the units chosen and conveniently provides a **Bulk Density Lookup Tool** with densities for common catalyst materials on the right side of the Excel spreadsheet and bottom of the web tool module. The fifth input, &quot;Planned reactor configuration&quot; accepts values of &quot;Fixed Bed&quot; and &quot;Slurry/Fluidized Bed&quot; and affects the calculation of attrition losses mentioned above, since fluidized beds cause greater catalyst attrition. The sixth input, &quot;Has trace Sn, Cu, Fe \&gt; 2% of AP?&quot; addresses the difficulty of recovering precious metals from catalysts contaminated with over 2% (by wt. % of the active phase) of any of the named metals, and triggers a &quot;metal contaminant&quot; fee in addition to fees charged to catalysts without these contaminants. The seventh and final input, in contrast to the forgoing inputs, determines to the sale value, if any, and landfill cost of the spent catalyst. It is entitled &quot;Classification for Sale or Landfill&quot; and accepts options such as &quot;Zeolite, Silica, Alumina&quot; and &quot;Hazardous (e.g., RCRA metals).&quot; For more information on the meaning of these options and selecting the appropriate classification for a catalyst, see the following sections.

![](RackMultipart20210611-4-vy292y_html_43a4c1d5e2fb826e.png)

**Figure 9.2.** Inputs section of **4 Spent Catalyst** module in Excel, showing an estimate completed for a Rh/C catalyst.

  1.
## Spent Catalyst Recovery/Disposal Details and Calculation Logic

    1.
### Overview of options for managing spent catalyst

Figure 9.3 illustrates commonly available options for managing spent catalyst and key decision points for each. This decision logic has been incorporated in CatCost such that the options mentioned below are automatically selected to maximize spent catalyst value. In general, spent catalysts can be sent to a catalyst refiner and processed to reclaim metals, sold for other uses (e.g., steel, cement, or smelter), or disposed of in a landfill. Note that it is already assumed that plants employing catalytic materials will regenerate them as long and as often as it is economical to do so. Starting at the top of Figure 9.3 (&quot;START&quot;), spent hydrotreating and fluidized catalytic cracker (FCC) catalysts used in petroleum refineries are generally landfilled or sometimes sold to a cement or steel mill. Hydrotreating catalysts are designated as hazardous waste by the US Environmental Protection Agency (EPA) through the Resource Conservation and Recovery Act (RCRA),29 but if properly stabilized, can be deemed safe to handle and transport. These materials, once properly pretreated, can be regenerated, sold for their Mo, V or W content to be used in steel, or landfilled. FCC catalysts are generally not considered hazardous and do not require stabilization due to the highly encapsulated nature of the catalyst structure. For non-hydroprocessing/hydrorefining catalysts, the first step is to determine whether or not the spent material is hazardous waste (per RCRA and/or state regulations). If it is, the material may either be sent to a hazardous landfill, or it is possible that it may be sold to a catalyst refiner if there is enough PGM and they are equipped to process the material. For non-hazardous material, it first goes through a thermal oxidation step to remove residual volatiles, coke, and most of the sulfur resulting from catalytic processing. For non-PGM catalysts, it may or may not be economically justified to reclaim metals (e.g., Ni, Co, Cu) from the spent material. If the recovery option is chosen, the type of processing used will depend on the support. For Al2O3, SiO2 or carbonate supports, the support is first solubilized with an appropriate solvent (e.g., NaOH or H2SO4). The metals are then recovered from the insoluble residue via filtration, and hydrometallurgical processing is used to further purify and recover the metals. For clay, BaSO4, TiO2, and ZrO2 supports, the metals are leached (e.g., with a HCl / sodium chlorate mixture) from the support and then concentrated into a solution form for recovery and purification. For a metal &quot;sponge&quot; in which a high-surface-area metal is used as a catalyst with no supporting material, the sponge is first calcined and then solubilized and recovered similarly to silica- and alumina-supported catalysts.

For PGM catalysts, (see &quot;PGM CATALYST&quot; in Figure 9.3), it must first be decided whether or not to recover the metal, which depends on the identity of the PGM(s) and amount present in the spent material. Generally, if the material contains less than 0.2% PGM, the recovery option will be uneconomical and/or technically difficult. In this case, the material could either be landfilled or sold to a smelter or catalyst refiner (to add to their stockpile for later refining). If the recovery option is chosen, the processes described above for the oxide supported materials are applied. For carbon supported material, the initial thermal oxidation step destroys the support and the remaining metal is dissolved and recovered via hydrometallurgy.

![](RackMultipart20210611-4-vy292y_html_f3d97183e4db93c2.gif)

**Figure 9.3.** Spent catalyst management options and associated costs.

The mathematical logic used for calculation of aggregated costs for each of the spent catalyst options is described in the following paragraphs. Default values for the key variables used in these calculations are given in the tables contained in the Spent Catalyst Library (described in Section 9.3).

    1.
### Metals Recovery Option:

If the option to reclaim spent catalyst is chosen, the value associated with reclaiming metal from the spent catalyst is counted as a credit towards the manufacturing cost to calculate an overall adjusted catalyst cost:

Where is the overall adjusted cost of the catalyst in $/lb catalyst purchased with and defined below.

= manufacturing cost ($/lb catalyst purchased)

= reclaimed catalyst value ($/catalyst purchased)

is calculated as:

is the salvage value of the metal ($/lb catalyst purchased) and is calculated as

Where

= metal loss from use phase (lb metal lost/lb metal on fresh catalyst)

= metal loss from catalyst refining process (lb metal lost/lb metal on spent catalyst)

= metal loading on catalyst (lb/lb fresh catalyst)

_P_ = metal spot price ($/lb)

is the cost to recover the metal ($/lb catalyst purchased) and is calculated by summing the fees for each of the processing steps shown in the block diagrams (Figure 9.3) (thermal oxidation, dissolution/leaching and hydrometallurgy, and refining charge for Platinum Group Metal (PGM) catalysts):

Where

= thermal oxidation fee ($/lb catalyst treated)

= incoming fee for metals recovery processing (typically dissolution/leaching + hydrometallurgy) (lb/ft3 catalyst treated)

_ρ_ = catalyst bulk density (lb/ft3)

= refining fee ($/lb PGM metal recovered)

is the total catalyst solids lost during the use phase (resulting from loading, attrition, metal not staying attached, and unloading), (lb catalyst loss/lb fresh catalyst), and is calculated as:

Where

= loss of support during use phase (lb support/lb fresh catalyst)

CatCost default values for the variables used in the above equations are given in Section 9.3.

    1.
### Sale Option:

If the spent catalyst is sold for other purposes, the overall Adjusted Catalyst Cost is calculated as:

Where is the sale value available from various buyers. The applicable sale values are given in Section 9.3.

In the case of a molybdenum containing catalyst, is calculated as

Where

= Loading of Mo on catalyst (lb Mo/lb catalyst purchased)

= Price of MoO3 ($/lb)

0.15-0.40 (adjustment factor, fraction of MoO3 value)

(Factor of 1.5 is the molecular weight ratio of MoO3 to Mo)

    1.
### Landfill Option:

If neither metals recovery nor sale is a viable option for a spent catalyst, it must be landfilled at additional cost. This is particularly likely in the following scenarios:

1. Hydroprocessing and hydrorefining catalysts are deemed RCRA hazardous waste by the US EPA but can be treated/stabilized to render the waste non-hazardous and subsequently disposed of in a non-hazardous waste landfill.
2. If a spent catalyst contains any of the RCRA metals (&quot;Big 8&quot;), Toxicity Characteristic Leaching Procedure (TCLP) testing is needed to determine whether or not it is hazardous waste. The TCLP limits are provided in the Spent Catalyst Library (next section) (hazardous determination is accomplished solely through testing and working with a company&#39;s regional regulatory authorities).
3. If a PGM catalyst contains less than 0.2% PGM, the PGM cannot be easily recovered so it would likely go to landfill.

The adjusted catalyst cost in the case of the landfill option is calculated as:

Where is the overall cost to landfill ($/lb catalyst purchased) and is calculated as:

Where

is the landfill fee ($/lb catalyst landfilled)

Typical landfill fees included in CatCost are given in Section 9.3.

  1.
## The Spent Catalyst Library

The Spent Catalyst Library included in CatCost provides default values for the variables used in calculations in **4 Spent Catalyst,** as described in the previous section. The user may change or add to the entries in the Spent Catalyst Library to suit their estimation needs. The Spent Catalyst Library contains the same information described below, but implemented into five tables with slightly different grouping and different numbering than in this report.

Table 9.1 gives average losses of the support and active phase metal during catalyst use, which are used in the calculation of spent catalyst solids remaining after unloading of the reactor. Table 9.2 presents typical metal losses that occur during catalyst refining. Table 9.3 lists average thermal oxidation and incoming fees charged for the different support types. Table 9.4 lists typical fees charged by the catalyst refiner. Table 9.5 lists estimated catalyst bulk densities. The Toxicity Characteristic Leaching Procedure (TCLP) limits are listed in Table 9.6 and include a 20-fold dilution of waste (weight basis) in acetic acid, per EPA Test Method 1311.30 Also listed are the corresponding minimum concentrations of metals that would need to be present in the spent catalyst material to possibly exceed the TCLP limits (assuming 100% of the metal leaches out of the spent catalyst). This table is provided here and in CatCost for informational purposes only and hazardous determination is accomplished solely through testing and working with the proper regulatory authorities. The list of applicable landfill fees for calculation of spent catalyst disposal is listed in Table 9.7. Table 9.8 presents typical selling prices for spent catalyst sold for other uses, such as cement, a smelter, or metals refiner.

**Table 9.1.** Average values of support and metal losses from use phase.

| **Support** | **Fixed** | **Slurry/Fluidized** |
| --- | --- | --- |
|
 |
 |
 |
 |
 |
| TiO2 | 2% | 10% | 3% | 13% |
| ZrO2 | 2% | 10% | 3% | 13% |
| SiO2 | 2% | 3% | 2% | 4% |
| Al2O3 | 2% | 3% | 2% | 4% |
| Carbon | 2% | 2.5% | 6% | 5% |
| Carbonate | 5% | 5% | 5% | 5% |
| Sponge of metal | n/a | 5% | n/a | 5% |
| Clay | 5% | 5% | 5% | 5% |

**Table 9.2.** Metal loss from refining.

| **Metal** | **High** | **Low** | **Average** |
| --- | --- | --- | --- |
| _ **PGMs** _ |
| _Palladium_ | 4% | 1% | 3.5% |
| _Platinum_ | 3% | 1% | 3.0% |
| _Rhodium_ | 10% | 5% | 7.5% |
| _Ruthenium_ | 25% | 15% | 20.0% |
| _Gold_ |
 |
 | 10.0% |
| _Iridium_ |
 |
 | 10.0% |
|
 |
 |
 |
 |
| _ **Non-PGMs** _ |
| Aluminum
 (Claus, misc) |
 |
 | 70% |
| Cobalt |
 |
 | 20% |
| Copper CuZn | 25% | 15% | 20% |
| Iron |
 |
 | 40% |
| Molybdenum | 30% | 20% | 25% |
| Nickel |
 |
 | 20% |
| Silver | 2% | 3% | 2.5% |
| Tungsten NiW | 25% | 15% | 20% |

**Table 9.3.** Thermal oxidation fees (_F__thermox_) and incoming fees (_F__incoming_) for metals recovery processing (typically dissolve/leach + hydrometallurgy).

| **Process/ Variable** | **Support** | **(low) $/lb** | **(high) $/lb** |
| --- | --- | --- | --- |
| _Thermal Oxidation_ | All | 0.125 | 0.15 |
|
 |
| **Process / Variable** | **Support** | **(low) $/ft****3 **|** (high) $/ft ****3** |
| _Incoming Fee for Processing_ – (\&lt;2% Cu, Fe, Sn of PGM) | Carbon | 94 | 115 |
| Al2O3, SiO2, TiO2, ZrO2, carbonate, clay | 108 | 123 |
| Sponge_a_ | 81 | 92 |
| _Incoming Fee for Processing_– (\&gt;2% Cu, Fe, Sn of PGM)_b_ | Carbon | 115 | 130 |
| Al2O3, SiO2, TiO2, ZrO2, carbonate, clay | 126 | 137 |
| Sponge_a_ | 95 | 103 |

_a_ Estimated at 30% less costly than with hard supports.

_b_ Applies to catalysts that contain Cu, Fe, or Sn at \&gt;2% of the main PGM or non-PGM metal.

**Table 9.4.** Refining Charge - .

| Metal | $/TrOz
 Recovered |
| --- | --- |
| Pt | 14.5 |
| Pd | 12.5 |
| Rh | 16 |
| Au | 11 |
| Ru | 20 |
| Ir | 25 |
| Ag | 11.5 |

**Table 9.5.** Catalyst bulk densities provided to users as a guide.

| **Catalyst** | **ρ (lb/ft****3****)** | **Note** |
| --- | --- | --- |
| Activated C powder | 42 | Containing 50% moisture |
| Activated C granules | 46 | Containing 50% moisture |
| Metal on Al2O3 | 45 | dry extrudate |
| Metal on TiO2 | 65 | dry extrudate |
| Metal on ZrO2 | 66 | dry extrudate |
| Al2O3/SiO2, 44%/51% | 50 | dry extrudate |
| SiO2, 3/16&quot; | 30 | dry spheres |
| Sponge Ni, Co, or Cu | 71.25 | Dry basis; average of 67.5-75 lb/ft3 |

**Table 9.6.** RCRA metals and Toxicity Characteristic Leaching Procedure limits, along with _estimated_ minimum concentrations in a catalyst that would be expected to cause a material to exceed the TCLP limit and be regulated under RCRA.

| **Metal** | **TCLP Limit, mg/L** | **Minimum Concentration in Catalyst, wt%** |
| --- | --- | --- |
| As | 5 | 0.01% |
| Ba | 100 | 0.20% |
| Cd | 1 | 0.002% |
| Cr | 5 | 0.01% |
| Pb | 5 | 0.01% |
| Hg | 0.2 | 0.0004% |
| Se | 1 | 0.002% |
| Ag | 5 | 0.01% |

**Table 9.7.** Landfill Fees (_F__landfill_).

| **Catalyst Type** | **Fee (per pound catalyst)** | **Notes** |
| --- | --- | --- |
| Zeolite, Silica, Alumina | $0.15-0.20/lb | e.g., FCC |
| Ni/Mo, Co/Mo, Ni/W | $0.75/lb | Includes stabilization |
| PGM | $1-3/lb | May include stabilization |
| Hazardous Waste | $1-3/lb | E.g., contains Big 8\&gt;TCLP limits |

**Table 9.8.** Sale Values (_V__sale_)

| **Catalyst Type** | **Value** | **Notes** |
| --- | --- | --- |
| Zeolite, Silica, Alumina | $0.05/lb catalyst | e.g., for cement |
| PGM | $1-1.30/lb catalyst | e.g., to smelter or refiner, typically \&lt;0.2% PGM |
