---
uid: Connector_help_GitHub_Repositories_Technical
---

# GitHub Repositories

## About

This DataMiner connector allows you to monitor and control GitHub repositories. It uses the GitHub API to poll the repos and execute actions on them.

![General](~/connector/images/GitHub_Repositories_General_Page.png)

## Getting Started

### Step 1: Deploy the Connector

1. Click the **Deploy** button on the [Catalog page](https://catalog.dataminer.services/details/eece1db3-7a77-4182-bc0a-40e9158efc90) to deploy the connector directly to your DataMiner System.
1. Optionally, go to [admin.dataminer.services](https://admin.dataminer.services/) and verify whether the deployment was successful.

### Step 2: Create an Element

1. Open DataMiner Cube and navigate to the *Surveyor* module.
1. Right-click a view and select *New* > *Element*.
1. Enter a name for your element.
1. Select the **Github Repositories** protocol and the latest version.
1. Fill in `https://api.github.com` as the IP address/host.
1. Click *Create*.

### Step 3: Configure the Element

1. Go to [Github.com](https://github.com).
1. Sign in and go to *Settings* > *Developer settings* > *Personal access tokens* > *Tokens (classic)*.
1. Generate a new token.
1. Go back to the element and enter the API Key parameter on the *General* > *Configuration* page.

### Step 4: Add a GitHub Repository (Optional)

1. Go to the *Repositories* page of the element.
1. Right-click the table and select *Add*.
1. Fill in the name and owner of the repository.
1. Click *OK*.

## Contributing

To contribute to this connector, create a fork on Github and create a pull request. Skyline Communications will do a code review as soon as possible and merge the suggestions.

## Support

For additional help, reach out to [arne.maes@skyline.be](mailto:arne.maes@skyline.be)
