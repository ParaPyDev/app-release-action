# ParaPy Application Release GitHub Action

![ParaPy Logo](https://s3-eu-west-1.amazonaws.com/parapy-cache/wp-content/uploads/2016/12/22134017/Logo_margin.png)

This GitHub Action is provided by [ParaPy](https://parapy.nl) to test ParaPy applications.

Example workflow:

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
            license-key: ${{ secrets.PARAPY_LICENSE_KEY_1 }}
            license-certificate: ${{ secrets.PARAPY_LICENSE_KEY_2 }}
            parapy-pypi-username: ${{ vars.PARAPY_PYPI_USERNAME }}
            parapy-pypi-password: ${{ secrets.PARAPY_PYPI_PASSWORD }}
            parapy-cloud-address: "<company-parapy-cloud-address>"
            service-account-identifier: ${{vars.PARAPY_SERVICE_ACCOUNT_CLIENT_ID }}
            service-account-secret: ${{vars.PARAPY_SERVICE_ACCOUNT_SECRET }}
            parapy-app-identifier: ${{vars.PARAPY_APP_ID }}
            parapy-app-version: ${{ inputs.version }}
            deploy: ${{ inputs.deploy }}
```
