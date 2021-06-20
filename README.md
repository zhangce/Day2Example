# Day2Example

## Serving APIs

Each Aim is has one serving API, which you can use to get predictions. 
For this aim, the API is

    https://....../Day2Example?features=[...]
    https://....../Day2Example?batch=[...]

The API will return the predictions of all deployed models:

    [{ model1: "yes", model2: "no", ...}...]

## Deployed Models

Deployed models are a collection of models that are used for each call to the 
serving API.

All deployed models are stored in the branch `deployed_models`.

## Deployment Candidates

All Deployed Models are choosen from a set of deployment candidates,
which are stored in the branch `deployment_candidates`.

A user can manually choose to commit deployment candidates to deployed models.

A user can call Model picker, which takes as input the current deployment candidates
and deployed models, and produce a new set of deployed models. This creates a new 
commit in the branch `deployed_models`.

## Trial

Each Trial is identified by one unique training set `uploaded` by the user. 
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

The user might choose to move some models in each trial to the deployment 
candidate branch. This creates a new commit in the `deployment_candidates` branch 
and is where CI/CD gets triggered. 

## Validation Set

All trials in an Aim shares the same validation dataset, which is stored in
its own branch `validation_set`.

## Production Set

Each call to the serving APIs will be logged and use as the fresh 
production set. By defaulted they are not logged in git.



