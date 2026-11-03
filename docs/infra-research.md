# Infrastructure Research Notes

## 1. Renovate

Renovate automates dependency and Docker image updates.

The existing Infra configuration includes:

- Scheduled updates on Saturday after 10 PM.
- Docker image digest pinning.
- A maximum of five concurrent pull requests.
- Grouped updates for selected application stacks, including Hermes, Twenty and n8n.
- Dashboard approval for major updates.
- Exclusion of camofox-browser because it is locally built.

## 2. GitHub Runners

GitHub runners execute automated workflows.

The existing infrastructure notes report that three older self-hosted runner containers were stopped.

The reusable CI workflows use self-hosted runners, so their current availability needs to be verified before reuse.

## 3. Container Registry

The Infra documentation identifies GHCR as the intended image registry.

The existing reusable CI release workflow publishes images to Docker Hub.

The final registry choice and shared registry availability need confirmation from Fenil.

## 4. Pending Work

- Verify current runner availability.
- Confirm the approved container registry.
- Review image publishing requirements.
- Understand Renovate's scheduled execution.
- Coordinate deployment configuration with Fenil.

## 5. Scope

These notes are based on the reviewed Infra and CI workflow repository snapshots. They do not confirm the current live infrastructure status.