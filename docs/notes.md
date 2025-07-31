# General Research Notes Captured During Template Creation

---
## New Installation Steps

1. 


---
## Scaffold Customizations Necessary After Standard `helm create`

1. `helm create _-_-_-_CHART_-_NAME_-_-_-_` creates and minimally populates a new chart directory
   with the specified name. Name must match regex `^[a-zA-Z0-9._-]+$`, so pick a name that can be
   searched and replaced unambiguously, e.g.: `_-_-_-_CHART_-_NAME_-_-_-_`
2. mkdir ./admin
   1. create ./admin/secrets.yaml file
3. mkdir ./config

---
## The Bitnami Charts Template ❌
See https://github.com/bitnami/charts/tree/main/template

This seems to be more complicated than we need. For example, it includes references to MariaDB,
placeholder subcharts, a StatefulSet.yaml in addition to Deployment.yaml, and many more. It also
contains a bunch of placeholders of the form `%%PLACEHOLDER_HERE%%` - see below -- which cause the
`helm create -p` command to fail. 

We can start with a simpler template and add complexity as needed.

### List of placeholders in the Bitnami template at: ~/dev/GITHUB/BITNAMI/charts/template/CHART_NAME

These prevent use of the template directly by the `helm create -p` command from working, implying
this is not really a valid "scaffold" template in its original form. 

```shell
$ grep -r "%%[^%]*%%" . | sed -e 's/.*\(%%[^%]*%%\).*/\1/g' | sort | uniq
%% EXPLAIN INTEGRATION. CHECK OTHER EXAMPLES %%
%%CHART_NAME%%
%%CHOOSE_ONE_FROM_CHART_CATEGORIES_FILE%%
%%COMPONENT_NAME%%
%%CONFIG_FILE_NAME%%
%%CONTAINER_NAME%%
%%DESCRIPTION%%
%%ENTRYPOINT and CMD from main container%%
%%IF NEEDED%%
%%IMAGE_NAME%%
%%IMAGE_REVISION%%
%%IMAGE_TAG%%
%%INTRODUCTION%%
%%Instructions to access the application depending on the serviceType and other considerations%%
%%MAIN_CONTAINER%%
%%MAIN_CONTAINER/POD_DESCRIPTION%%
%%MAIN_CONTAINER_NAME%%
%%MAIN_OBJECT_BLOCK%%
%%MAJOR_SUBCHART_VERSION_(A.X.X)%%
%%OTHERS_CONTAINER/POD_DESCRIPTION%%
%%OTHER_OBJECT_BLOCK%%
%%OTHER_PARAMETERS_RELATED_TO_THIS_CONTAINER/POD%%
%%OTHER_PARAMETERS_RELATED_TO_THIS_SUBCHART%%
%%OTHER_SECTIONS%%
%%PORT_NAME%%
%%SAME_STRUCTURE_AS_THE_MAIN_CONTAINER/POD%%
%%SECONDARY_CONTAINER/POD_DESCRIPTION%%
%%SECONDARY_OBJECT_BLOCK%%
%%SUBCHART_CONTAINER/POD_DESCRIPTION%%
%%SUBCHART_NAME%%
%%TEMPLATE_NAME%%
%%UPSTREAM_PROJECT_KEYWORD%%
%%UPSTREAM_PROJECT_SOURCE_CODE_URL%%
%%UPSTREAM_PROJECT_VERSION%%
%%commands%%
%%httpGet || command || etc%%
```
