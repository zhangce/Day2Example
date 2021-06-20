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
