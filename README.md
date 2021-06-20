# Day2Example

## Serving APIs

Each Aim is has one serving API, which you can use to get predictions. 
For this aim, the API is

    https://....../Day2Example?features=[...]
    https://....../Day2Example?batch=[...]

The API will return the predictions of all deployed models:

    [{ model1: "yes", model2: "no", ...}...]

## Deployed Models

Deployed models are a collection of models that each call to the API will 
use to answer each call to the Serving APIs.

All deployed models are stored in the branch `deployed_models`.

## Deployment Candidates

All Deployed Models are choosen from a set of deployment candidates,
which are stored in the branch `deployment_candidates`.

## Trial

Each Trial is identified by one unique training set uploaded by the user. 
Each trail has its own branch. Each commit in the trial branch contains:

  - training set: The state of the training set
  - search space: The search space of AutoML
  - models: The results of all models
  - other meta data, e.g., labeling functions

Every call to "What's Next" will create a set of suggested transformations.
Each transformation takes as input one commit in a trail and bring it to 
a new commit:

  - new training set: after data cleaning, labeling etc.
  - new search space
  - new models
  - new meta data



