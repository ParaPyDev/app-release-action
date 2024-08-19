# ParaPy Application Release GitHub Action

This GitHub Action is provided by ParaPy to easily release and deploy ParaPy applications, to your ParaPy Cloud, with GitHub actions.

Example workflow, utilizing the Action:

```yaml
name: Release a new version of your application
on: 
  workflow_dispatch:
    inputs:
      version:
        description: 'Application version to release'     
        required: true

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
            parapy-cloud-address: "<company-name>.parapy.nl"
            service-account-identifier: ${{vars.PARAPY_SERVICE_ACCOUNT_CLIENT_ID }}
            service-account-secret: ${{vars.PARAPY_SERVICE_ACCOUNT_SECRET }}
            parapy-app-id: ${{vars.PARAPY_APP_ID }}
            parapy-app-version: ${{ inputs.version }}
            test: true
            deploy: false
```
