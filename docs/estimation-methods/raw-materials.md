# Materials Costs: The 2 Materials Module and Materials Library

## Overview

The **2 Materials** module of CatCost, coupled with the **Materials Library**, allows the convenient addition of raw materials to an estimate. This module allows the selection of a material from the library, conversion of units, and automatic stoichiometric and cost calculations. The first step to entering a synthesis into the **2 Materials** module is to define the scale by completing the fields in the &quot;Materials Calculation Inputs&quot; section of the module that include the stoichiometric parameters of a synthesis (Figure 4.1). The first input, &quot;Yield Type,&quot; has three possible values: &quot;% Yield,&quot; &quot;Catalyst Mass,&quot; or &quot;AP [Active Phase] Mass.&quot; Depending on this selection, the user enters either a % yield or a mass yield of catalyst or active phase in the next input cell. For the &quot;% Yield&quot; option, a molecular weight for the active phase and a stoichiometric ratio of the mols of active phase per mol of metal precursor must also be entered. The &quot;% Yield&quot; option assumes that the combined molar quantity of metal precursors entered into the synthesis comprise the limiting reagent. Next, the user enters the &quot;Active Phase Weight Percent.&quot; The last input on the Materials Calculation Inputs is &quot;Losses Due to Waste/Spoilage,&quot; which accounts for inevitable losses during storage and handling.

TODO: screenshot needed?

**Figure 4.1.** The **2 Materials** module in the Excel version of CatCost, showing the entry of stoichiometric parameters and individual raw materials with automated unit conversions and lookups from the Materials Library.

The user may then proceed to add materials to the estimate by selecting an empty cell in the &quot;Material Name&quot; column of &quot;Metal Sources,&quot; &quot;Supports,&quot; or &quot;Other Materials&quot; and using the dropdown button to select a material from the Materials Library. The user then enters a consumption for that material by typing both a quantity and a unit, which will automatically be converted to the estimate mass units. If a volume unit is entered but the Materials Library does not contain a density for that material, the calculation will fail with a &quot;No Density&quot; message. For the user&#39;s convenience, the quantity for the first entry in the Supports table is pre-populated with a formula that calculates the required quantity of a single support to achieve the specified weight loading. This can be overwritten by the user.

The default **Materials Library** of CatCost includes a large library of high-volume chemicals obtained from the ICIS Indicative Price Library. The **Materials Library** is designed to allow users to easily add new materials by adding a row to the table. Input fields in the **Materials Library** include the following (see notes in _italic type_):

- Material Name
- Material Type – _used for record-keeping only at present_
- Molecular Weight (MW), g/mol – _used in stoichiometry calculations on &quot;2 Materials&quot;_
- Density (g/mL) – _used for unit conversions on &quot;2 Materials&quot;_
- Concentration (%) – _for record-keeping only at present_
- Lab-Scale Log Fit? – _if &quot;Lab&quot; is selected, a lab-scale log fit is performed_
- Lab-Scale Columns – _show/hide using +/– at top_
  - Lab Quantity 1–4 – _must use same units, entered in &quot;Lab Units&quot;_
  - Lab Units
  - Lab Price 1–4 – _this is a_ _total_ _price, i.e., the price for the quantity of the material specified in the corresponding Lab Quantity column,_ _not_ _a unit price_
- Bulk Quote Price
- Bulk Quote Quantity
- Bulk Quote Units
- Quote Year – _used for price escalation to the estimate basis year_
- Quote Source
- Quote Access Date – _used for record-keeping only_
- Notes

Making selections and entries in these fields allows the **Materials Library** to automatically perform unit and price calculations. Users are encouraged to add their own materials to the library and to consider keeping their own &quot;master copy&quot; of CatCost with a library of materials appropriate to their estimates. For more details on the calculations performed by CatCost in **2 Materials** and the **Materials Library**, see the following sections.

## Materials Consumption

Materials consumption calculations in CatCost rely on information from the pre-commercial or lab-scale synthesis of the catalyst of interest. The user supplies the lab-scale quantity of each reagent.

This laboratory-scale reaction stoichiometry serves as the basis of a materials balance and is scaled by CatCost to user-specified quantities. CatCost employs information about the yield and stoichiometry of the synthesis of interest to determine the scaling factor required to convert the user-input lab-scale quantities to the targeted plant design scale in mass units (_M__cat_; capital letters indicate plant design scale). The required information includes the reaction yield (_yield_), the stoichiometric ratio of the active phase to limiting reagent (_mol__AP __/mol__ LR_) in the balanced reaction formula (e.g., synthesis of Mo2C from a reaction-limiting monometallic Mo precursor would have _mol __AP__ /mol__LR_ = 0.5), and the molecular weights of both the limiting reagent (_MW__LR_) and the catalyst active phase as formulated in the balanced reaction formula (_MW__AP_). These inputs allow determination of the active-phase mass at lab scale (_m__AP_) (eq 4.1).

(4.1) TODO eqn

The total catalyst mass at lab scale (_m__cat_) can then be defined as the sum of the contributions of the active phase (_m__AP_) and the support material (_m__sup_) (eq 4.2).

(4.2) TODO eqn

While the user may supply the mass of support material, if the supporting operation that generates the finished catalyst is assumed to be efficient (100% yield with no discarded support material or active phase), the _m__sup_ can be restrained using the user-input weight percent loading (_wt%_) of active phase in the catalyst (eq 4.3).

(4.3) TODO eqn

The scaling factor (_k__SF_) is then defined using the lab-scale (_m__cat_) and plant design scale (_M__cat_) catalyst mass quantities (eq 4.4).

(4.4) TODO eqn

Each material&#39;s consumption (in any unit) at lab scale can then be scaled to the plant design scale in the same unit by multiplication with the (unitless or year–1) scaling factor.

## Materials Pricing

When planning catalyst manufacture, the best source for a raw material price is a quote from a credible supplier matching the characteristics of the actual purchase arrangement (e.g., quantity, purity, order frequency, delivery method, and location) most probable for the proposed plant. However, because many of these factors will be uncertain at the time of inquiry and suppliers may be reluctant to undertake the cost of a detailed estimate for a hypothetical purchasing plant that is very early in the design process, such price quotes may be difficult to obtain. Many CatCost users also lack access to in-house price databases used at catalyst companies for cost estimation.

Accordingly, freely available bulk pricing, industry catalog data, and, where necessary, extrapolation from lab-scale supplier pricing, are important for simple and rapid catalyst cost estimates. Among these methods, bulk prices (&quot;bulk&quot; scale is considered to be ≥ one ton) available on marketplace websites such as Alibaba may be useful because they already incorporate the best current market information. However, they may be systematically higher than the final settlement price of a transaction after negotiation.9 When available, proprietary databases like the Process Economics Program (PEP) provided via subscription by IHS Markit Ltd are often useful. CatCost contains freely available prices from the ICIS Chemical Business catalog provided by the RELX Group.10 In general, these databases do not include a comprehensive list of specialty chemicals and are especially lacking in the areas of inorganic and organometallic chemicals. In cases where none of the aforementioned databases provides a credible price, the final two raw materials cost estimation methods, extrapolation from lab scale and in-house synthesis, can be used.

The first method employed for estimation of the cost of raw materials without bulk pricing information is extrapolation from lab-scale pricing. While lab-scale chemical supplier pricing reflects specific investment in that supply scale and order quantity1 and is therefore not ideal for bulk price prediction, it has the advantage of ready availability on supplier websites. Furthermore, previous work by researchers at LBNL9 has established suitable parameters and conditions under which this method provides acceptable accuracy in predicting bulk unit prices.

In the extrapolation method for bulk cost estimation, multiple lab-scale prices are fit to a power function (eq 4.5) relating the unit price _p_ (obtained by dividing the quote price _P_ by quote quantity _Q_) to quantity _Q_ with two parameters. Using the terminology proposed by the authors of the LBNL report,9 these parameters are the quantity discount factor (_γ_) and scaling parameter (_b_). In practice, fitting is done by log-log linear regression to _p_ and _Q_ data points, which yields _γ_ as the fit slope and _b_ as the fit intercept.

(4.5) TODO eqn

An example of log-log regression fitting for a common metal precursor is shown in Figure 4.2. A series of price quotes from Acros Organics (through Fisher Scientific)11 for nickel(II) acetate tetrahydrate in quantities ranging from 100 g to 2.5 kg was used to extrapolate the price of bulk Ni(OAc)2•4H2O. The linear regression was performed on log10(_p_) (_p_ = _P_/_Q_) vs. log10(_Q_) and produced _γ_ = -0.363, _b_ = 1.803, and _p_(2,000 lb) = 4.04 $/lb. This calculated bulk price compares favorably to an independently obtained bulk price quote from Alibaba,12 which was not included in the linear regression. The bulk price quote lists $8,250–10,000/tonne for Ni(OAc)2•4H2O, which is equivalent to _p_ = 3.74–4.54 $/lb. A plot of _p_ vs. _Q_ for the lab- and bulk-scale price quotes, including the calculated _p_(_Q_) trendline, is shown in Figure 4.2a. The same information is shown in Figure 4.2b with logarithmic axes, and the details of the calculation are tabulated in Figure 4.2c.

The second method for estimation of raw material costs in the absence of bulk pricing data is an in-house synthesis approach. Without assuming that the raw material would actually be produced in the catalyst synthesis plant through a sub-process, the method of breaking down a raw material into its own synthetic feedstocks and processing steps (using the methods described throughout this section) provides an alternative method of estimation when no other information is available. This approach requires knowledge of likely synthetic routes to the raw material of interest, as well as pricing information for the sub-process inputs. In the case of precious metal salts, it is often a good approximation to simply value the salt using the prevailing price of the metal content, perhaps with a small percentage added to cover the conversion from the most common form of that metal to the desired salt/precursor.

![](RackMultipart20210611-4-vy292y_html_6372a498e87d6ca1.gif) TODO img

![](RackMultipart20210611-4-vy292y_html_879f8af1de74d66a.gif) TODO img

![](RackMultipart20210611-4-vy292y_html_b8c08f39ddd13e64.png) TODO img

**Figure 4.2.** Log-log linear regression fit to lab-scale price quote data (2016) for Ni(OAc)2•4H2O: a) plot of _p_ vs. _Q_ including indicative power fit, b) log-log plot of _p_ vs. _Q_ including linear regression fit showing agreement with bulk price quote (red), and c) details of price data and linear fit.
