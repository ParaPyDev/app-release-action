# ParaPy Application Release GitHub Action

<a href="https://parapy.nl" rel="ParaPy">![ParaPy](https://s3-eu-west-1.amazonaws.com/parapy-cache/wp-content/uploads/2016/12/22134017/Logo_margin.png)</a>

This GitHub Action is provided by [ParaPy](https://parapy.nl) to release ParaPy applications.

Example workflow (*with recommended usage of [secrets](https://docs.github.com/en/actions/security-for-github-actions/security-guides/using-secrets-in-github-actions)/[vars](https://docs.github.com/en/actions/writing-workflows/choosing-what-your-workflow-does/store-information-in-variables) usage for the different parameters*):

```yaml
name: Release your application
on: 
  workflow_dispatch:
    inputs:
      version:
        description: 'Application version to release'     
        required: true
    deploy:
        description: 'Whether to deploy the application if the release is successful'
        type: boolean
        default: false

jobs:
  application-release:
    runs-on: ubuntu-20.04
    steps:
    - uses: parapydev/app-release-action
        with:
            license-key-1: ${{ secrets.PARAPY_LICENSE_KEY_1 }}
            license-key-2: ${{ secrets.PARAPY_LICENSE_KEY_2 }}
            parapy-pypi-username: ${{ vars.PARAPY_PYPI_USERNAME }}
            parapy-pypi-password: ${{ secrets.PARAPY_PYPI_PASSWORD }}
            parapy-cloud-address: "<company-parapy-cloud-address>"
            service-account-identifier: ${{vars.PARAPY_SERVICE_ACCOUNT_CLIENT_ID }}
            service-account-secret: ${{ secrets.PARAPY_SERVICE_ACCOUNT_SECRET }}
            parapy-app-identifier: ${{ vars.PARAPY_APP_ID }}
            parapy-app-version: ${{ inputs.version }}
            deploy: ${{ inputs.deploy }}
```

Please find descriptions for each parameter in the [pipeline specification](action.yaml).
