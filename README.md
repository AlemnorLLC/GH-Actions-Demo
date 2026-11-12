# GH ActionsDemo

## GitHub Actions workflows

These example workflows demonstrate build and test automation, pull request checks, security scanning, artifact packaging, deployment setup, and artifact provenance.

| Workflow | Trigger | Description |
| --- | --- | --- |
| `01-hello-world.yml` | Every push | Checks out the repository and prints a sample build message. |
| `02-build-test.yml` | Every push | Sets up .NET 10, restores dependencies, builds in Release configuration, and runs tests. |
| `03-pr-validation.yml` | Pull requests targeting `main` | Runs the .NET 8 restore, Release build, and test steps as a pull request check. |
| `04-codeql.yml` | Pull requests targeting `main` | Initializes CodeQL for C#, autobuilds the project, and uploads analysis results for security scanning. |
| `05-dependency-review.yml` | Pull requests targeting `main` | Runs GitHub's dependency review action to check dependency changes. |
| `06-package.yml` | Every push | Publishes the .NET application in Release configuration, archives the output as `application.tar.gz`, and uploads it as the `application-package` artifact. |
| `07-environment-deploy.yml` | Pushes to `main` | Targets the `production` environment and prints a placeholder message. Configure environment protection rules in GitHub to require approval; this example does not perform a deployment. |
| `08-oidc-deploy.yml` | Manual (`workflow_dispatch`) | Requests an OIDC token, logs in to Azure using the `AZURE_CLIENT_ID`, `AZURE_TENANT_ID`, and `AZURE_SUBSCRIPTION_ID` repository secrets, then displays the active Azure account. It demonstrates authentication rather than deploying an application. |
| `09-attestation.yml` | Every push | Creates a sample tarball, uploads it as `application-package`, and generates a build-provenance attestation for the archive. |
| `10-attestation-verification.yml` | Manual (`workflow_dispatch`) | Downloads the `application-package` artifact for the run and verifies `application.tar.gz` provenance for this repository with GitHub CLI. The artifact must be available to the verification run. |

The workflows are independent examples; the two artifact workflows use a sample archive and do not form an automatic build-to-deploy pipeline.
