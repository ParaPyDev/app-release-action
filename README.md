# ParaPy Application Release GitHub Action

This GitHub Action is provided by ParaPy to test ParaPy applications.

Example workflow:

```yaml
name: Test your application
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
    runs-on: ubuntu-latest
    steps:
    - uses: parapydev/app-release-action
        with:
            license-key: ${{ secrets.PARAPY_LICENSE_KEY_1 }}
            license-certificate: ${{ secrets.PARAPY_LICENSE_KEY_2 }}
            parapy-pypi-user-name: ${{ vars.PARAPY_PYPI_USERNAME }}
            parapy-pypi-password: ${{ secrets.PARAPY_PYPI_PASSWORD }}
            parapy-cloud-address: "<company-parapy-cloud-address>"
            service-account-identifier: ${{vars.PARAPY_SERVICE_ACCOUNT_CLIENT_ID }}
            service-account-secret: ${{vars.PARAPY_SERVICE_ACCOUNT_SECRET }}
            parapy-app-id: ${{vars.PARAPY_APP_ID }}
            parapy-app-version: ${{ inputs.version }}
            deploy: ${{ inputs.deploy }}
```
