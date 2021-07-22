# Two Methods for Processing Cost Estimation

CatCost contains two distinct methods for estimating &quot;processing&quot; costs in a catalyst synthesis. Processing costs can be understood to include all non-materials costs of an industrial synthesis, including capital equipment purchase and ongoing maintenance, plant design and construction, land purchase and upkeep, labor, process utilities, and other components of capital and operating costs. Estimating processing costs is the most complex and difficult part of assembling a catalyst cost estimate. In order to provide flexibility to users, CatCost includes two distinct approaches to estimating processing costs. These two approaches, the [Step Method](/estimation-methods/step-method) and the [CapEx & OpEx Factors](/estimation-methods/capex-and-opex-factors) method, are summarized below. All estimation methods assume production in the United States with respect to environmental regulations, default entries for regionally varying costs such as operating labor, and other aspects of production.

[Step Method](/estimation-methods/step-method) _(note: Excel version only in CatCost v1.1.0)_

- Assumes production at a contract catalyst manufacturer (&quot;toller&quot;)
- Uses all-in hourly costs of operation in $/hour
- Requires a list of process steps and an order size in tons
- Based on methods used by tollers to provide price quotes
- Provides rapid estimates
- Modules: **3a Step Method**

[CapEx & OpEx Factors](/estimation-methods/capex-and-opex-factors)

- Assumes construction of a new, dedicated catalyst plant for catalyst synthesis
- Uses detailed estimation of &quot;primary&quot; costs and fixed percentages for &quot;secondary&quot; costs
- Requires a list of process equipment including sizes, quantities, materials of construction, and auxiliary equipment such as pumps and motors, as well as process utilities consumption, and a production scale (e.g., kg/year)
- Based on estimating methods from the chemical engineering process design literature
- Provides detailed estimates that require more time and specialized knowledge to prepare
- Modules: **3b Equipment**, **3c Utilities**, **3d CapEx**, and **3e OpEx**

Within CatCost, these two distinct methods are implemented separately as noted in the Modules bullets in the list above. When choosing a processing cost estimation method, the user should then complete only those modules listed for that method above. CatCost also allows the user to use both methods in a single estimate, for example using the convenience of the Step Method to evaluate the addition of a single process step to an existing process design assembled in CapEx &amp; OpEx Factors. This is accomplished by the inclusion of a combined outputs section in the main CatCost outputs, described below. The two methods could also be completed using similar process steps to allow a comparison between them and thus between the scenarios of toller manufacturing and new-build synthesis plant. _**If combining the two methods (rather than comparing them), it is critical that no process step be entered in both methods, or this will overestimate the cost of producing catalyst (i.e., if a synthesis has 5 steps and steps #4 and #5 are entered in the Step Method, those steps should NOT be entered in CapEx &amp; OpEx Factors).**_
