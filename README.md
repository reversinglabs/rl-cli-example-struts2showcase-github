# ReversingLabs rl-secure GitHub Actions Examples

This repository contains working examples of GitHub workflows to illustrate scanning with the [ReversingLabs Spectra Assure CLI](https://docs.secure.software/cli/).

ReversingLabs Spectra Assure CLI is capable of scanning [nearly any type](https://docs.secure.software/concepts/language-coverage) of software artifact or package that results from a build.

In these examples, we're using the source code and Maven build instructions for the Struts2 showcase web app,
which came with [Apache Struts v2.5.28](https://archive.apache.org/dist/struts/2.5.28/).

The following examples are provided in the `.github/workflows` directory:

- **rl-scan-docker.yml**
- **rl-scan.yml**
- **rl-scan-docker-only.yml**
- **rl-scan-docker-self-hosted.yml**


All examples require that you create the `RLSECURE_ENCODED_LICENSE` and `RLSECURE_SITE_KEY` secrets to store your ReversingLabs [license and site key](https://docs.secure.software/cli/deployment/rl-deploy-quick-start#prepare-the-license-and-site-key).
You can define the secrets either in your GitHub repository or in the GitHub organization settings.


## rl-scan-docker.yml

This workflow builds the WAR file and scans it with the CLI using the [ReversingLabs rl-scanner Docker image](https://hub.docker.com/r/reversinglabs/rl-scanner).

The workflow is configured to be triggered manually only.

After the file is scanned, analysis reports in HTML, JSON, CycloneDX, and SPDX formats are published as an artifact called "ReversingLabs reports".


## rl-scan.yml

This workflow is similar to `rl-scan-docker.yml`, but it does not use the Docker image.
Instead, it installs the [rl-deploy](https://pypi.org/project/rl-deploy/) Python package, which is subsequently used to install and license the `rl-secure` CLI.

The workflow is configured to be triggered manually only.

After the file is scanned, analysis reports in HTML, JSON, CycloneDX, and SPDX formats are published as an artifact called "ReversingLabs reports".


## rl-scan-docker-only.yml

This workflow shows how to use the **[reversinglabs/gh-action-rl-scanner-only](https://github.com/marketplace/actions/gh-action-rl-scanner-only)** GitHub Action that relies on the `reversingLabs/rl-scanner` Docker image to scan the build artifact.


## rl-scan-docker-self-hosted.yml

This workflow verifies that the [ReversingLabs rl-scanner Docker image](https://hub.docker.com/r/reversinglabs/rl-scanner) can run with a self-hosted runner.

In particular, you have to verify what versions of local actions are supported by your version of GitHub Enterprise.

