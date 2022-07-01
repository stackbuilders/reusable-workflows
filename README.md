# Reusable Workflows

GitHub Actions [reusable workflows][reusable-workflows].

## Usage

The following section describes the usage of the different reusable workflows
offered by this repository.

### [cabal-upload](.github/workflows/cabal-upload.yml)

Uploads source package and documentation to Hackage.

```yml
jobs:
  call-cabal-upload:
    uses: stackbuilders/reusable-workflows/.github/workflows/cabal-upload.yml@main
    with:
      ghc_version: "8.10"
      cabal_version: "3.6"
      ignore_uploaded_package: true
    secrets:
      HACKAGE_USERNAME: ${{ secrets.HACKAGE_USERNAME }}
      HACKAGE_PASSWORD: ${{ secrets.HACKAGE_PASSWORD }}
```

### [eb-deploy](.github/workflows/eb-deploy.yml)

Creates a zip file via git archive and deploys an application version via
[beanstalk-deploy][beanstalk-deploy]


```yml
jobs:
  call-eb-deploy:
    uses: stackbuilders/reusable-workflows/.github/workflows/eb-deploy.yml@main
    with:
      environment_name: production
      environment_url: https://example.com
      eb_application_name: example
      eb_environment_name: example-production
      eb_region: us-east-1
    secrets:
      AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
      AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}
```

## License

MIT, see [the LICENSE file](LICENSE).

## Contributing

Do you want to contribute to this project? Please take a look at our
[contributing guideline](docs/CONTRIBUTING.md) to know how you can help us
build it.

---
<img src="https://www.stackbuilders.com/media/images/Sb-supports.original.png" alt="Stack Builders" width="50%"></img>  
[Check out our libraries](https://github.com/stackbuilders/) | [Join our team](https://www.stackbuilders.com/join-us/)

[beanstalk-deploy]: https://github.com/einaregilsson/beanstalk-deploy
[reusable-workflows]: https://docs.github.com/en/actions/using-workflows/reusing-workflows
