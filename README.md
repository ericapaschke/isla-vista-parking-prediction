# Isla Vista Parking Occupancy Prediction

Parking in Isla Vista, my college town, runs over 100% capacity - more cars than
legal spaces. To better understand when and where spaces actually open up, and to
help people spend less time circling for one, I built a model that predicts which
streets are most likely to have an open space, given the month, whether it's a
weekday or weekend, and the time of day.

The model is a random forest trained on roughly 18,000 on-street parking
observations across 122 street segments, collected by the Isla Vista Community
Services District with Dixon Resources Unlimited between April 2023 and March 2024.

## Live App

The project began as a predictive model, and I then built it into a web tool so
people could actually use the results to help them find parking.

The tool can be accessed at:

**[ivpark.org](https://ivpark.org)**

It is also featured on the [Isla Vista Community Services District website](https://islavistacsd.ca.gov/do-you-need-a-car-in-isla-vista) under transportation resources.

## Approach

- **Target:** whether a block face is under 90% occupied
- **Predictors:** month, day of week, hour, street, curbside inventory, and each block's geographic position
- **Models compared:** logistic regression, decision tree, and random forest, selected on cross-validated ROC AUC
- **Validation:** 75/25 stratified split, with 5-fold cross-validation on the training set
- **Deployment:** R Shiny with a Leaflet map ranking streets by predicted availability

## Project Output

The full project report and analysis can be viewed here: [View Project](https://ericapaschke.github.io/isla-vista-parking-prediction/)

The report documents the original model. The deployed version was refined
afterward — letting it distinguish individual streets rather than grouping the
less-observed ones, and adding each block's geographic position — which improved
held-out accuracy from about 71% to 79%.
