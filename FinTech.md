<font size=6 color=gray> (Part one) </font>
## <font color=IndianRed>Sample, variables, and methodology</font>

- ### <font color=Deepskyblue>Sample: Baidu Search and Database</font>
- ### <font color=Deepskyblue>Variables</font>: 
  1. <font color=Deepblue>Credit risk</font>
  2. <font color=Deepblue>FinTech</font>
      <font color=Plum>Employs the word frequency statistics of text mining(Four steps)</font>
        - Collect cities and keys (bank(origin)->city(now))
        - Calculate the original keywords' frequency
        - Choose the factor analysis method to construct the FinTech index (FT). and KMO tests and Bartlett test check if there are shared factors among the original keywords
        >  <font color=skyblue>To ensure that the indexes are positive, the maximum-minimum processing is applied to standardize data between 0 and 1, and FTAit, FTBit, FTCit, FTDit, and FTIit are obtained.</font>
         - evaluates the constructed result of the FT.
  3. <font color=Deepblue>Control variables</font>

        | Variables   | Description |
        | ----------- | :-----------: |
        | $Size_{i}$     | logarithm of total size for city $i$.     |
        | $Liquidity_{i}$   | the ratio of total bank loans to total deposits for bank $i$ |
        | $Overhead_{i}$     | logarithm of overheads for bank $i$     |
        | $CIR_{i}$   | the ratio of total bank cost to total income for bank $i$    |
        | $NIM_{i}$     | the ratio of net interest income to the average size of interest-earning assets for bank $i$     |
        | $Ownership$   | Ownership is a dummy variable that is equal to 1 if a city is direct controlled municipality, and 0 otherwise    |
        | $List$ (optional)    | a dummy variable that is equal to 1 if a bank has gone public and 0 otherwise     |
- ### <font color=Deepskyblue>Methodology</font>
    $$
    \mathrm{NPL}_{\mathrm{it}}=\text { Constant }+\mathrm{a} * \text { FinTech }_{\mathrm{it}}+\mathrm{b} * \text { Controlit }+\text { City }_{\mathrm{i}}+\varepsilon . \text { Model }
    $$
---
<font size=6 color=gray> (Part two) </font>

## <font color=IndianRed>Empirical results</font>
- ###  <font color=Deepskyblue>Descriptive statistics</font>
- ### <font color=Deepskyblue>Effects of Bank FinTech on credit risk</font>
  1. Test the multicollinearity of our explanatory variables(variance inflation factors (VIFs))
  2. Determine whether our data require the utilization of panel estimation or pooled estimation techniques
  3. a Hausman test to choose between fixed effects model and random effects model 
- ### <font color=Deepskyblue>Endogenous issue(?)</font>
- ### <font color=Deepskyblue>Robust tests (Need more info)</font>




