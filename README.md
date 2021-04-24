# Salesforce SFDX CLI action

This action allows to use the Salesforce SFDX CLI from GitHub Actions

## Inputs

### `sfdx-auth-url`

**Optional** Authorize a Salesforce org using an SFDX auth URL

The secret must have the format `force://<refreshToken>@<instanceUrl>` or `force://<clientId>:<clientSecret>:<refreshToken>@<instanceUrl>`

You can obtain the URL from a authorized org from your local machine using: `sfdx force:org:display -u ORG-ALIAS --verbose`

## Example usage

```yaml
name: SFDX Test Run on Push

on: [push]

jobs:
  test:
  
    runs-on: ubuntu-latest
    
    steps:
      - uses: hectorgb/sfdx-action@v1
        with:
          sfdx-auth-url: ${{ secrets.AUTH_SECRET }}
      - name: sfdx-test-run
        run: sfdx force:apex:test:run -l RunLocalTests -w 30
```
