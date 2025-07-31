## Helm Template for Deploying on Kubernetes Clusters

- **Authors**: Brooke, Matthew (https://orcid.org/0000-0002-1472-913X); ...
- **License**: [Apache 2](http://opensource.org/licenses/Apache-2.0)
- [Package source code on GitHub](https://github.com/DataONEorg/k8s-helm-template)
- [**Submit Bugs and feature requests**](https://github.com/DataONEorg/k8s-helm-template/issues)
- Contact us: support@dataone.org
- [DataONE discussions](https://github.com/DataONEorg/dataone/discussions)

This is a template to facilitate creation of new Helm charts, for deploying on Kubernetes clusters. It provides a scaffold for the basic structure and files needed to create a Helm chart, including configuration files, Kubernetes manifests, and documentation.

DataONE in general, and this template in particular, are open source, community projects.  We [welcome contributions](./CONTRIBUTING.md) in many forms, including code, graphics, documentation, bug reports, testing, etc.  Use the [DataONE discussions](https://github.com/DataONEorg/dataone/discussions) to discuss these contributions with us.

## Documentation

Documentation is a work in progress, and can be found here in the README.md file (how to use this template), and in the [docs](./docs) directory (research/background/decisions etc.)

## Usage Example

1. Copy the `helm` directory into your target repo, and perform the following renaming and replacement steps to reflect your repo name:

2. Find values for the variables below, to reflect your project-specific naming:
  - `APP_FULL_NAME` (all lowercase a to z; dashes allowed; no other special characters or spaces): the official full name of your application (typically your GH repo name) - e.g. `notification-service`.
  - `APP_ABBREV_NAME` (all lowercase a to z; no special characters or spaces): an abbreviated version of your application name. Keep it as short as possible, without introducing ambiguity (e.g. for `notification-service`, abbreviate to `notifications`; don't use `ns`).
  - `ENV_PREFIX`: (all UPPERCASE A to Z; no special characters or spaces): a prefix for any environment variables that will be set in the container. This should be a short, uppercase string, e.g. `NS` for `notification-service`.
  - 


3. then run the commands in your terminal:
```shell
# Assuming your official application name (typically your GH repo name) is "notification-service", for example:
APP_FULL_NAME=notification-service
APP_ABBREV_NAME=notifications
ENV_PREFIX=NS

# Find and replace only in text files, excluding binary 
# files, and dot-files (e.g. `.gitignore`) & dirs (e.g. `.git/`) 
find . -type f \
  ! -path "./.*" \
  ! -path "./.*/*" \
  -exec grep -Iq . {} \; -exec sed -i '' \
    -e "s/%%APP_FULL_NAME%%/${APP_FULL_NAME}/g" \
    -e "s/%%APP_ABBREV_NAME%%/${APP_ABBREV_NAME}/g" \
    -e "s/%%ENV_PREFIX%%/${ENV_PREFIX}/g" \
    {} +
```

4. Finally, clean up all the leftover informational comments that are no longer needed. Keep your Helm chart clean and simple, so that it's easy to read and understand!

## License
```
Copyright [2024] [Regents of the University of California]

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

https://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

## Acknowledgements
Work on this package was supported by:

- DataONE Network
- Arctic Data Center: NSF-PLR grant #2042102 to M. B. Jones, A. Budden, M. Schildhauer, and J. Dozier

Additional support was provided for collaboration by the National Center for Ecological Analysis and Synthesis, a Center funded by the University of California, Santa Barbara, and the State of California.

<a href="https://dataone.org">
<img src="https://user-images.githubusercontent.com/6643222/162324180-b5cf0f5f-ae7a-4ca6-87c3-9733a2590634.png"
  alt="DataONE_footer" style="width:44%;padding-right:5%;">
</a>
<a href="https://www.nceas.ucsb.edu">
<img src="https://www.nceas.ucsb.edu/sites/default/files/2020-03/NCEAS-full%20logo-4C.png"
  alt="NCEAS_footer" style="width:44%;padding-top:3%;padding-bottom:3%; background-color: white;">
</a>
