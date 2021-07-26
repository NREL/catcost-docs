# Processing Costs via a Detailed CapEx &amp; OpEx Factors Method: The _3b Equipment_, _3c Utilities_, _3d CapEx_, and _3e OpEx_ Modules and _Equipment Library_

## Overview

The second approach to processing cost in CatCost is a detailed, factored processing cost estimation method, entitled CapEx &amp; OpEx Factors. This approach, in contrast to the step method described in the previous chapter, assumes the construction of a dedicated process plant to synthesize the catalyst in question. The CapEx &amp; OpEx Factors method allows significantly more detail and potentially more targeted insight than the step method, but requires more time and specialized knowledge/tools (e.g., AspenPlus) to generate. However, we have reduced these demands dramatically for common catalyst types by inclusion of process templates (Chapter 8).

The potential accuracy and flexibility benefits of a factored processing cost estimate result from the explicit consideration of a wide range of capital and operating components of processing cost. The methods for inclusion in CatCost were identified primarily through review of the process design literature used by chemical engineers for cost estimation. The methods selected for inclusion have been extensively used and validated, which means detailed information is available on the accuracy of each method and the associated error of each component for sensitivity analysis.

In this chapter, the methods are presented first and the implementation of these methods in CatCost is found in the last section.

## Simplifying Estimates with Primary and Secondary Categories

In the process design literature, preliminary cost estimates for a new-build chemical synthesis plant are commonly made using a factored approach. This involves estimating a few components, which we will call &quot;primary&quot; costs, in detail and using factors (i.e., percentages) of the primary components to determine the other, &quot;secondary&quot; components.4,6,19-23 The primary components commonly include raw materials purchase cost, direct operating labor cost, and equipment purchase cost. The secondary components comprise a wide variety of costs, such as ongoing supervisory labor or capital cost for piping, that tend to vary linearly with a particular primary component, within a known range. The accuracy afforded by this approach is on the order of ± 15 % up to ± 40 % (commonly called &quot;preliminary&quot; or &quot;study-grade&quot; in design literature),5,6 which is appropriate for inclusion in CatCost.

Following this literature precedent, the procedure for estimating a catalyst cost using CatCost can be defined by three steps: (1) From the lab-scale synthesis procedure, develop a list of unit operations (e.g., jacketed, agitated reactor, spray dryer, ball mill) needed to conduct the synthesis at industrial scale. (2) Using the list of operations and the synthesis information, price primary components such as raw materials purchase cost, delivered-equipment purchase cost, ongoing direct labor, etc. (3) For secondary costs that vary directly with one of the primary outputs, use a factor (i.e., a percentage) to determine those costs from the primary output. This concept is depicted in Figure 7.1, which shows secondary components of capital cost being determined as factors of the primary component, purchased equipment cost.

![](RackMultipart20210611-4-vy292y_html_9e933f892109db18.jpg)

**Figure 7.1.** Illustration of the concept of determining secondary cost components as factors (percentages) of primary cost components, such as delivered purchased-equipment cost, that are first calculated in detail.

## Determining Primary Costs: Capital

Capital cost estimation for process plants begins with pricing each unit of process equipment. Equipment purchase cost is widely estimated by scaling a known price for a similar piece of equipment to the specific size needed in a process.4,19-23 Rather than scaling linearly, these prices tend to follow power-law relationships (eq 7.1) with 0.6 being a common value for exponent _a_. The specific exponents to use for various pieces of equipment have been tabulated most extensively by Garrett and range from 0.38 to 0.90.24 This method therefore requires only a valid price quote for each equipment type. For scaling purposes, the size of equipment is typically measured by a flowrate, heat-transfer area, volume, power rating, etc. Some authors have improved the accuracy of the scaling method by incorporating more than one parameter for a particular equipment type.8,22,25 For example, Ulrich and Vasudevan scale process vessels not by volume alone, but as a function of both height and width to account for the relatively larger material requirements of extreme shapes.22 It is also common to include factors for the cost of various materials of construction, e.g., carbon steel, stainless steel, aluminum. Importantly, some authors also include an exemplary price quote for each equipment type,19,24 allowing complete algebraic determination of equipment cost at arbitrary size (within the extrapolation limits of these methods), which is what is needed for incorporation into CatCost.

(7.1) TODO EQN

A number of these equipment pricing methods have been compiled into web- or spreadsheet-based costing tools, most of which also facilitate the calculation of secondary costs (buildings, piping, installation, etc.) based on purchased-equipment cost. A useful review of these pricing tools has been published by Feng and Rangaiah.25 Thus, there is precedent for the type of equipment costing used in CatCost.

CatCost includes a library of equipment cost correlations to allow the expert user to develop an equipment list and associated capital cost estimate from scratch. This library also forms the basis of the process templates (next chapter) so that users without design experience will be able to simply select a catalyst synthesis type, such as wet impregnation, zeolite, metal-organic framework, etc. and have the equipment list auto-populated. Equipment cost correlations in the Equipment Library take one of two forms: a power-law form (eq 7.2) derived from eq 7.1 or a poly-exponent form (eq 7.3),8 in which a, b, c, d, e, and n are constants used to fit empirical cost data and _S_ is a sizing input parameter, such as volumetric capacity in gallons.

(7.2) TODO EQN

(7.3) TODO EQN

## Determining Primary Costs: Operating

Direct labor cost is the most common primary component of operating costs in published estimation methods.4,22,23 Direct labor is defined here as the sum of labor requirements of each process unit. Items like supervisory labor and laboratory / quality assurance are figured as factors of direct labor. Direct labor can be readily calculated for a particular piece of process equipment _i_ using the formula in eq 7.4. The (Operator Hours / Equipment Hours)_i_ variable represents direct labor requirements for that piece of equipment; a value of 1.0 would indicate one full-time operator per process unit; a value of 0.5 would indicate an operator splitting his/her time between two units of this type. The local productivity adjusts the operator/equipment ratio to local labor productivity figures, which vary regionally. Both of these values are available in chemical engineering design texts.4,22,23 The local hourly labor rate can be freely obtained from the U.S. Bureau of Labor Statistics or corresponding bodies abroad.

(7.4) TODO EQN

## Determining Secondary Costs with Factors

The third and final step of processing cost estimation, determination of factored or secondary costs, is applied to capital costs using the equipment costs as primary components. This general approach was first described by Lang,26,27 who proposed that the total capital cost of a process plant could be estimated as between 3.10 and 4.74 × the total purchase cost of the major equipment items. The disadvantage of this approach is that it is not very accurate or process-specific. Progress was made by Hand28 and later by Guthrie,19 who proposed different factors for each type of equipment. These were called &quot;module factors&quot; by Guthrie because they give the total installed cost, including materials and labor, of the entire process unit (i.e., the module) relative to the equipment purchase price alone. These methods make the overall estimate more process-specific and therefore more accurate but are not very complete in terms of equipment types covered. Garrett, on the other hand, provided a set of both module factors and installation factors (similar to the module factors but omitting related minor equipment and piping) for a wide range of equipment types.24 We found Garrett&#39;s set of installation costs to be the most comprehensive single set of numbers, to agree generally with the variation in installation costs for different equipment types provided by other equipment-specific sources,19,22,28 and to fall within the range (when used within exemplary catalyst estimates) established by Lang-type methods4,26,27 for the components covered. Separately, Peters and Timmerhaus updated the original Lang approach to provide a breakdown for an overall process plant, including direct capital costs like installation, piping, instrumentation, and buildings; indirect costs like engineering, legal, and contingencies; and working capital.4 However, like the original Lang factors, the Peters and Timmerhaus method does not account for the specific types of equipment included in the plant. In CatCost, we have implemented a hybrid approach that achieves process specificity by using the equipment-specific installation factors of Garrett,24 while using the factors of Peters and Timmerhaus4 for all other components of capital cost. This approach allows the user to see how much, for example, installation labor or equipment insulation contributes to product cost.4,22,23 This concept is depicted in Figure 7.1 and exemplary factors from two references are shown in Table 7.1. The table displays the slight variation in categories and factor values that is common in the literature. Furthermore, the user can customize the ranges used in the estimation to improve the usefulness of the sensitivity information this method provides.

| **Table**  **7****.1.** Determination of secondary cost components from primary components in plant capital cost estimation: exemplary factors from literature. |
| --- |
| **Capital Cost Factors** Delivered Purchased-EquipmentInstallationInstrumentation and ControlsPiping (installed)Electrical (installed)BuildingsYard ImprovementsService FacilitiesEngineering and SupervisionConstruction FeesContingency **Total Fixed Capital** Working Capital **Total Capital Investment** | **Factor – ref.**  **4** **(%)**100_a_39–4718–3616–68_b_10–1118–2510–1540–7032–3334–4135–44 **397–504** 70–89 **467–593** _c_ | **Factor – ref.**  **23** **(%)**100_a_30–6020–3020–8015–2015–3020–3030–4020–30not included_d_30 **455–605** not included_d_ **455–605** |
| _a_By definition. _b_ There are more detailed, but still deterministic, methods for accurately estimating components that tend to vary widely, like piping costs.
_c_ Since working capital is recovered at the end of the plant lifetime (though this inflow must be discounted), including it here gives the total upfront capital cost.
_d_ These categories from reference 4 are grouped into other categories in reference 23. |

For estimation of secondary components in operating costs, direct labor is the most common basis (e.g., for items like laboratory costs and benefits) but other bases are also important. For example, total capital cost is among the best predictors for items like maintenance costs and certain utilities. Some items, such as energy costs, rely on equipment-specific requirements and modeling the local cost of energy commodities.

For each of the secondary cost categories, CatCost provides situation-dependent low, average, and high values for the determining factor. These values represent a synthesis and update of the various literature references to guide user input and form the basis of future sensitivity analyses. These values are intended to be a starting point for users to adjust and learn about the effect of these factors on their catalyst cost estimates.

## Implementation in CatCost

The processing cost methods described above were incorporated into a functional, extensible, and user-friendly CapEx &amp; OpEx Factors method within CatCost. This method allows detailed and accurate cost estimations while automating much of the process to reduce the time required to generate an estimate.

### The _3b Equipment_ Module and Equipment Library

The foundation of the CapEx &amp; OpEx Factors method in CatCost is the equipment list for the industrial catalyst synthesis process, found in module **3b Equipment.** This equipment list generates or influences the majority of capital and operating cost components in CatCost and corresponds naturally to the process steps a catalyst engineer is accustomed to designing. The equipment module for a particular process template (see chapter 8 for details on process templates) is shown in Figure 7.2. It contains a section with template info and scaling inputs (Figure 7.2A), the main equipment list where equipment items are selected and sized (B), a section where equipment items are automatically scaled to the estimate production scale and costs generated (C), and cost and labor factor totals (D).

![](RackMultipart20210611-4-vy292y_html_d5898a702983b5e7.png)

**Figure 7.2.** The equipment list module for the Zeolite for FCC process template, showing the four sections: A) Template info and scaling inputs, B) equipment list with equipment selection and sizing inputs, C) automated scaling to estimate production rate, and D) totals section.

In the scaling section (Figure 7.2A &amp; Figure 7.3), inputs on the throughput of the equipment list specified in the equipment selection and sizing inputs section (Figure 7.2B) are entered. This information is analogous to that in the Materials Calculation Inputs section of **2 Materials.** The information entered in &quot;THIS PROCESS Design Production Rate&quot; tells CatCost the catalyst production throughput of the process represented by the equipment list in Figure 7.2B. Separately, the &quot;ESTIMATE Design Production Rate&quot; is looked up from **1 Inputs.** As a result, the user is able to change the Design Production Rate on **1 Inputs** and this will cause CatCost to automatically scale the entered equipment list from the scale of &quot;THIS PROCESS Design Production Rate&quot; to the scale of &quot;ESTIMATE Design Production Rate.&quot; See below for details on scaling.

![](RackMultipart20210611-4-vy292y_html_129c3b5ff3bf8d11.png)

**Figure 7.3.** The template info and scaling inputs section of the equipment module.

In the main equipment list section (Figure 7.2B &amp; Figure 7.4), users select process equipment (such as &#39;Reactor, jacketed, agitated&#39;) from the CatCost Equipment Library, which we believe to be the largest free and publicly available library of costs for chemical process units. It contains over 200 pieces of equipment from respected sources.4,8,19,22-24 Equipment items are added by drop-down, as in **2 Materials.** For equipment added to the list, CatCost prompts the user for a sizing parameter, such as tank size in m3 or pump power in kW. It also allows the user to select the material of construction for each piece of equipment according to process requirements, such as corrosion resistance. The material of construction selection causes CatCost to multiply that equipment item&#39;s by a material factor. For each equipment item, there is a base factor (e.g., carbon steel = 1.0) and other materials are relative to it (e.g., 316 stainless = 1.3; Hastelloy C = 1.55). The available materials depend on the equipment item.

![](RackMultipart20210611-4-vy292y_html_110e2f953b535bad.png)

**Figure 7.4.** The main equipment list section for a Zeolite for FCC process design, showing Equipment Type selection from the Equipment Library by dropdown list, User Label, Material of Construction, and the scaling inputs Quantity and Size. Note that the Size Unit from the Equipment Library is provided and varies between equipment items. Finally, a &quot;Within Size Limits?&quot; check is included to help users identify when their process design might be better suited by an alternate equipment type (the equipment will still be scaled automatically by CatCost even if outside the size limits range).

Based on the user inputs to the equipment list, CatCost automatically looks up and calculates key outputs for each equipment item and for the process plant as a whole. These outputs include the equipment purchase price, using established cost correlations that incorporate factors for varying materials of construction and which automatically notify the user of equipment which is sized outside the pricing correlation&#39;s range of validity; factors that multiply with the equipment purchase price to produce an installed cost (which includes the equipment and associated fittings, support structures, installation labor, etc.); and direct labor requirements for each piece of equipment (Figure 7.5).

![](RackMultipart20210611-4-vy292y_html_6ef956f59c0b9a34.jpg)

**Figure 7.5.** Screenshot of the main equipment list inputs and scaling outputs sections of the equipment module, showing the automated scaling built into CatCost. The jagged line indicates cells that are hidden. The equipment in the list has automatically been scaled from the reference design scale for this equipment list of 100 M lb/yr to this estimate&#39;s production scale of 300 M lb/yr. The outputs section contains purchase cost, installed cost, and a labor factor. Purchase cost is calculated using material of construction-specific pricing correlations and scaled from the correlation year to the estimate basis year. For each piece of equipment, factors for the number of labor operators and for installation cost as a multiple of purchase price are retrieved from the CatCost database.

Evaluating the effect of changing production scale is easy and automated in CatCost. It automatically adjusts the size of equipment items entered from the scale specified by &quot;THIS PROCESS Design Production Scale&quot; to the &quot;ESTIMATE Design Production Scale&quot; (see Figure 7.3 for the scaling inputs and Figure 7.5 for the scaling outputs). In Figure 7.5, an example that scales the Zeolite for FCC process from 100 M lb/yr to the estimate scale of 300 M lb/yr is shown. If this scaling sizes a piece of equipment below its pricing correlation&#39;s minimum size, the price of a minimum size unit is used; similarly, if the equipment called for is too large for a pricing correlation, CatCost automatically generates two or more of that piece of equipment to replace the oversized unit, while never using fewer than the number specified in the base case (i.e., if pumps are needed in two locations then at least two pumps are needed). The rest of the logic in the processing module carries these changes through, allowing a user to rapidly see how the fraction of catalyst cost contributed by, for example, capital investment changes with production scale. Figure 7.6 shows the results of scaling a 100 M lb/yr base case to two new production scales.

![](RackMultipart20210611-4-vy292y_html_f0e9a534f10147ef.jpg)

**Figure 7.6.** An example of the automated scaling incorporated into CatCost, which allows easy scenario analysis to observe the relative significance of, for example, capital investment to total product cost at various production scales.

Finally, the equipment cost totals section gives a summary of the equipment module calculations (Figure 7.2D &amp; Figure 7.7).

![](RackMultipart20210611-4-vy292y_html_e0aae08f2532f20.png)

**Figure 7.7.** Equipment cost totals section of the equipment module.

### The _3c Utilities_ Module

The **3c Utilities** module contains consumption inputs per unit catalyst and unit costs for six process utilities: cooling water, process water, low-pressure steam, high-pressure steam, electricity, and natural gas. The Excel version of the module is shown in Figure 7.8. Entries in this module should correspond to the process design entered on **3b Equipment.** The section shown in Figure 7.8 allows editing of the unit costs only; to edit the consumption values, there is a section for each process template (Figure 7.9; see chapter 8 for details on process templates).

![](RackMultipart20210611-4-vy292y_html_82d658e95bb52b38.jpg)

**Figure 7.8.** The **3c Utilities** module in the Excel version of CatCost.

![](RackMultipart20210611-4-vy292y_html_8d8fe92bd21f6685.png)

**Figure 7.9.** The consumption inputs section for the Zeolite for FCC process template in the Excel version of CatCost. In the upper section, inputs define how much catalyst (e.g., 1 lb catalyst, 1 kg active phase) the consumption values correspond to. In the lower section, consumption values are entered for each of six utilities.

### The _3d CapEx_ and _3e OpEx_ Modules

The outputs from the equipment list form the basis for estimation of the remainder of CatCost&#39;s processing cost components, as described in Section 7.5. In the factored capital costs module **3d CapEx,** cost components like piping, installation, buildings, land, etc. are calculated from the total equipment purchase price using percentage factors. Default factors are provided from Peters &amp; Timmerhaus,4 and the user can change any or all of the factors according to their own process design knowledge or to evaluate cost scenarios (Figure 7.10). The factored operating costs module on **3e OpEx** is similar (Figure 7.11), but with most costs based on the sum of direct labor requirements rather than the purchased equipment cost. The cost bases vary in the operating factors. Notably, Distribution and Marketing and Research and Development costs exclude the value of any precious/noble metals content using the **4 Spent Catalyst** module, so for catalysts containing these metals the calculation will not be complete until **4 Spent Catalyst** has been completed.

![](RackMultipart20210611-4-vy292y_html_e5f015e0db70e8ae.jpg)

**Figure 7.10.** Factored Capital Costs on **3d CapEx.**

![](RackMultipart20210611-4-vy292y_html_e1a649afd537a73.jpg)

**Figure 7.11.** Factored Operating Costs on **3e OpEx.**
