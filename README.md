# Project 2 proposal

Overall goal: create a linear regression model to predict the crude overdose mortality rate per county in 2016.

Primary data sources:
* Target variable: overdose mortality rate obtained from CDC WONDER databases
  * For number of deaths per county ranging between 10-20, the CDC classifies mortality rates as 'Unreliable' due to small event rate. For number of deaths per county ranging between 0-9, the CDC does not even give a value due to privacy concerns (e.g. these deaths could be identifiable); for these counties, the number of deaths is given the value of 'Suppressed'.
* Regressors: demographic and economic data; medical and legislative/political data as well if there is time to obtain this information
  * Census data (obtained from https://api.census.gov/):
    * Economic: median household salary, poverty rate (may have to convert this to Z-scores from the national average poverty rate for 2016, since otherwise percentage is a bounded variable between 0 and 100), percent unemployed
    * Demographic: median age, percentage white (again to be converted to Z-scores), percentage with education of high school graduate or higher
    * For the census data, most if not all of these regressors are related, therefore there is a high degree of collinearity. E.g., the poverty rate and the percent unemployed are clearly closely related, although they don't measure exactly the same thing.
  * Other sources:
    * Opioid prescribing rate map for 2016, located [here](https://www.cdc.gov/drugoverdose/maps/rxcounty2016.html); again from the CDC. Could also include the [map for 2015](https://www.cdc.gov/drugoverdose/maps/rxcounty2015.html) to see if that is more strongly predictive.
    * Number of methadone clinics per county: [directory](http://www.opiateaddictionresource.com/treatment/methadone_clinic_directory)
    * Either presence or absence of PDMP, or age of PDMP. Info located here: [State Profiles with links for each state](http://www.pdmpassist.org/content/state-profiles)
    * Number of bills passed by each state legislature that contains the word 'opioid'. Obtained from this [website](http://www.ncsl.org/research/telecommunications-and-information-technology/ncsl-50-state-searchable-bill-tracking-databases.aspx)
    * Cook Partisan Voting Index (PVI) for each county. Because Cook PVI is calculated per Congressional district, will instead use this [spreadsheet](https://docs.google.com/spreadsheets/d/1lpIJK1wHTSX3yw00vI_eUi6qpOq3yppozh_I5EdLLC4/edit#gid=0) from this [link](https://decisiondeskhq.com/news/2016-county-pvis-with-county-by-county-calculations/) from decisiondeskhq in order to get the PVI by county.
