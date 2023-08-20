# Deploy to Kinsta using GitHub Actions

## Introduction

Welcome to the GitHub Actions workflow for deploying WordPress themes — or any code for that matter — to Kinsta's hosting platform. This workflow was crafted with a vision rooted in simplifying the deployment process and providing a seamless solution for hosting sites on Kinsta. Our story is one of addressing challenges, embracing innovation, and creating a pathway for developers to effortlessly deploy themes while fostering collaboration and efficiency.

> Our journey began with a commitment to our clients who entrusted us with their WordPress sites hosted on Kinsta. We recognized the significance of creating a streamlined build and deployment process that could seamlessly adapt to their evolving needs. Fueled by our passion for innovation, we embarked on a quest to integrate our existing CI/CD approach on GitHub with the Kinsta platform.
> 

***- Chris Miller***

## Table of Contents

- [Introduction](#introduction)
- [Table of Contents](#table-of-contents)
- [Workflow Overview](#workflow-overview)
- [Usage](#usage)
- [Adding Secrets](#adding-secrets)
- [Workflow Details](#workflow-details)
- [Customization](#customization)
- [Contributing](#contributing)

## Workflow Overview

This GitHub Actions workflow simplifies the process of deploying WordPress themes to Kinsta environments using a continuous integration and continuous deployment (CI/CD) approach. The workflow consists of two main steps: **build** and **deploy**.

Kinsta separates its hosting environments by ports, ensuring a clear distinction between staging and production environments. This differentiation allows for controlled testing and secure deployment. Consequently, our workflow includes environment-specific secrets for the SSH ports, enabling a secure and accurate deployment process.

## Usage

1. Download the provided YAML file **`deploy-to-kinsta.yml`** from this repository.
2. Create a **`.github/workflows`** directory in your repository if it doesn't already exist.
3. Place the downloaded **`deploy-to-kinsta.yml`** file into the **`.github/workflows`** directory.
4. Customize the environment variables in the workflow to match your Kinsta setup.
5. Push the changes to your repository, and the workflow will automatically trigger on each push to the specified branches.

## Adding Secrets

For secure deployment, it's crucial to configure the following environment variables in your repository's secrets:

1. `STAGING_PRIVATE_KEY`: SSH private key for the staging environment.
2. `PROD_PRIVATE_KEY`: SSH private key for the production environment.
3. `SERVER`: Remote host server address.
4. `USERNAME`: Remote server username.

Additionally, given Kinsta's environment separation by ports, add the following secrets:

5. `STAGING_PORT`: SSH port for staging.
6. `PRODUCTION_PORT`: SSH port for production.
7. `STAGING_DIR`: Directory path on the staging server for deployment.
8. `PRODUCTION_DIR`: Directory path on the production server for deployment.

## Workflow Details

The workflow is divided into two stages:

1. **Build**: This stage prepares the theme files for deployment.
    - Installs Composer packages (if needed).
    - Sets up Node.js environment and installs dependencies.
    - Builds theme files and creates a zip archive.
2. **Deploy**: This stage uploads the theme to the appropriate Kinsta environment.
    - Downloads the built theme archive.
    - Unzips the archive.
    - Uses SSH to securely connect to the remote server.
    - Deploys the theme to the designated directory on the server.

## Customization

Feel free to customize the workflow to suit your project's requirements. You can modify the branches that trigger the workflow, adjust the environment variables, or extend the workflow with additional steps.

## Contributing

Contributions to this GitHub Actions workflow are welcome! If you have suggestions or improvements, feel free to submit a pull request.

---

*Proudly crafted by Prolific Digital*
