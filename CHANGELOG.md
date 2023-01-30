<!-- markdown-toc --bullets="-" -i CHANGELOG.md -->

<!-- toc -->

- [Next Release](#next-release)
  - [Summary of changes](#summary-of-changes)
    - [Go builder](#go-builder)
      - [New Features](#new-features)
    - [Generic generator](#generic-generator)
      - [New Features](#new-features-1)
    - [Container generator](#container-generator)
      - [New Features](#new-features-2)
  - [Changelog since v1.4.0](#changelog-since-v140)
- [v1.4.0](#v140)
  - [What's Changed](#whats-changed)
    - [Generic Generator](#generic-generator)
      - [Bug fixes](#bug-fixes)
    - [Go Builder](#go-builder)
      - [Bug fixes](#bug-fixes-1)
  - [New Contributors](#new-contributors)
  - [Full Changelog](#full-changelog)
- [v1.4.0-rc.2](#v140-rc2)
  - [What's Changed](#whats-changed-1)
  - [New Contributors](#new-contributors-1)
  - [Full Changelog](#full-changelog-1)
- [v1.4.0-rc.1](#v140-rc1)
  - [What's Changed](#whats-changed-2)
  - [New Contributors](#new-contributors-2)
  - [Full Changelog](#full-changelog-2)
- [v1.4.0-rc.0](#v140-rc0)
  - [What's Changed](#whats-changed-3)
  - [New Contributors](#new-contributors-3)
  - [Full Changelog](#full-changelog-3)
- [v1.2.2](#v122)
  - [What's Changed](#whats-changed-4)
  - [New Contributors](#new-contributors-4)
  - [Full Changelog](#full-changelog-4)
- [v1.2.1](#v121)
  - [What's Changed](#whats-changed-5)
    - [Generic generator](#generic-generator-1)
      - [buildType](#buildtype)
      - [Provenance file names](#provenance-file-names)
      - [Explicit opt-in for private repos](#explicit-opt-in-for-private-repos)
    - [Go builder](#go-builder-1)
      - [Support private repos](#support-private-repos)
  - [New Contributors](#new-contributors-5)
  - [Full Changelog](#full-changelog-5)
- [v1.2.0](#v120)
  - [What's Changed](#whats-changed-6)
    - [Generic generator](#generic-generator-2)
    - [Go builder](#go-builder-2)
  - [New Contributors](#new-contributors-6)
  - [Full Changelog](#full-changelog-6)
- [v1.1.1](#v111)
  - [What's Changed](#whats-changed-7)
  - [New Contributors](#new-contributors-7)
  - [Full Changelog](#full-changelog-7)
- [v1.0.0](#v100)
  - [What's Changed](#whats-changed-8)
  - [Contributors](#contributors)

<!-- tocstop -->

# Next Release

<!-- Information on the next release will be added here. -->

## Summary of changes

### Go builder

#### New Features

- A new [`upload-tag-name`](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/generic/README.md#workflow-inputs) input was added to allow users to specify the tag name for the release when `upload-assets` is set to `true`.
- The environment variables included in provenance output were changed to include only those variables that are specified by the user in the [slsa-goreleaser.yml configuration file](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/go#configuration-file) in order to improve reproducibility. See [#822](https://github.com/slsa-framework/slsa-github-generator/issues/822) for more information and background.

### Generic generator

#### New Features

- A new boolean [`continue-on-error`](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/generic/README.md#workflow-inputs) input was added which, when set to `true`, prevents the workflow from failing when a step fails. If set to true, the result of the reusable workflow will be return in the [`outcome`](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/generic/README.md#workflow-outputs) output.
- A new [`upload-tag-name`](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/generic/README.md#workflow-inputs) input was added to allow users to specify the tag name for the release when `upload-assets` is set to `true`.

### Container generator

#### New Features

- A new boolean [`continue-on-error`](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/container/README.md#workflow-inputs) input was added which, when set to `true`, prevents the workflow from failing when a step fails. If set to true, the result of the reusable workflow will be return in the [`outcome`](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/container/README.md#workflow-outputs) output.
- Support was added for authenticating with [Google Artifact Registry](https://cloud.google.com/artifact-registry) and [Google Container Registry](https://cloud.google.com/container-registry) using [Workload Identity Federation](https://cloud.google.com/iam/docs/workload-identity-federation). Users can use this new feature by using the [`gcp-workload-identity-provider` and `gcp-service-account` inputs](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/container/README.md#workflow-inputs)

## Changelog since v1.4.0

https://github.com/slsa-framework/slsa-github-generator/compare/v1.4.0...main

# v1.4.0

## What's Changed

This release is the first Generally Available version of the [Container Generator workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/container). The Container Generator workflow is now considered stable and can be included in your production GitHub Actions workflows

This is also the first release (technically the second) with support for the [generally available version of sigstore](https://blog.sigstore.dev/sigstore-ga-ddd6ba67894d)!!
We hope to have fewer issues with sigstore infrastructure moving forward.

### Generic Generator

#### Bug fixes

1. Allow users of the [Generic Generator](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/generic) to generate provenance for artifacts created in a project subdirectory (#1225)

### Go Builder

#### Bug fixes

1. Allow environment variables to contain '=' characters in the [Go builder](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/go) (#1231)

## New Contributors

- @cfergeau made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1232
- @DanAlbert made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1239
- @gal-legit made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1252

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.2.2...v1.4.0

# v1.4.0-rc.2

\*_This is a pre-release. It is not meant for general consumption. The following is the proposed release notes for the official release. _

## What's Changed

This release is the first Generally Available version of the [generic container workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/container). The generic container workflow is now considered stable and can be included in your production GitHub Actions workflows

This is also the first release with support for the [generally available version of sigstore](https://blog.sigstore.dev/sigstore-ga-ddd6ba67894d)!

This release also includes a couple of bug fixes:

1. Allow users of the [generic generator workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/generic) to generate provenance using for artifacts created in a project subdirectory (#1225)
2. Allow environment variables to contain '=' characters in the [Go workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/go) (#1231)

## New Contributors

- @cfergeau made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1232
- @DanAlbert made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1239
- @gal-legit made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1252

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.2.2...v1.4.0-rc.2

# v1.4.0-rc.1

\*_This is a pre-release. It is not meant for general consumption. The following is the proposed release notes for the official release._

## What's Changed

This release is the first Generally Available version of the [generic container workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/container). The generic container workflow is now considered stable and can be included in your production GitHub Actions workflows

This is also the first release with support for the [generally available version of sigstore](https://blog.sigstore.dev/sigstore-ga-ddd6ba67894d)!

This release also includes a couple of bug fixes:

1. Allow users of the [generic generator workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/generic) to generate provenance using for artifacts created in a project subdirectory (#1225)
2. Allow environment variables to contain '=' characters in the [Go workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/go) (#1231)

## New Contributors

- @cfergeau made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1232
- @DanAlbert made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1239
- @gal-legit made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1252

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.2.2...v1.4.0-rc.1

# v1.4.0-rc.0

**This is a pre-release. It is not meant for general consumption. The following is the proposed release notes for the official release.**

## What's Changed

This release is the first Generally Available version of the [generic container workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/container). The generic container workflow is now considered stable and can be included in your production GitHub Actions workflows

This is also the first release with support for the [generally available version of sigstore](https://blog.sigstore.dev/sigstore-ga-ddd6ba67894d)!

This release also includes a couple of bug fixes:

1. Allow users of the [generic generator workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/generic) to generate provenance using for artifacts created in a project subdirectory (#1225)
2. Allow environment variables to contain '=' characters in the [Go workflow](https://github.com/slsa-framework/slsa-github-generator/tree/main/internal/builders/go) (#1231)

## New Contributors

- @cfergeau made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1232
- @DanAlbert made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1239
- @gal-legit made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1252

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.2.2...v1.4.0-rc.0

# v1.2.2

## What's Changed

This release fixes issues with signing provenance due to a change in Sigstore TUF root certificates (#1163). This release also includes better handling of transient errors from the Rekor transparency logs.

## New Contributors

- @suzuki-shunsuke made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1061
- @datosh made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1074
- @pnacht made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1187
- @dongheelee92 made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/1209

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.2.1...v1.2.2

# v1.2.1

**DO NOT USE THIS RELEASE. This version will no longer work and is not supported due to errors described in #1163. Please upgrade to [v1.2.2](https://github.com/slsa-framework/slsa-github-generator/releases/tag/v1.2.2) or later.**

## What's Changed

This release fixes an error that occurs on the "Generate Builder" step for various workflows.

```
FAILED: SLSA verification failed: could not find a matching valid signature entry
```

See #942

### Generic generator

#### buildType

This release changes the [`buildType`](https://slsa.dev/provenance/v0.2#buildType) used in provenance created by the generic generator.

The previous value was:

```
"buildType": "https://github.com/slsa-framework/slsa-github-generator@v1",
```

The new value is:

```
"buildType": "https://github.com/slsa-framework/slsa-github-generator/generic@v1",
```

See #627

#### Provenance file names

Previously the default file name for provenance was `attestation.intoto.jsonl`. This has been updated to be in line with [intoto attestation file naming conventions](https://github.com/in-toto/attestation/blob/main/spec/bundle.md#file-naming-convention). The file name now defaults to `<artifact filename>.intoto.jsonl` if there is a single artifact, or `multiple.intoto.jsonl` if there are multiple artifacts.

See #654

#### Explicit opt-in for private repos

Private repository support was enhanced to required the `private-repository` input field as the repository name will be made public in the public Rekor transparency log.

Please add the following to your workflows if you opt into allowing repository names to be recorded in the public Rekor transparency log.

```yaml
with:
  private-repository: true
```

See #823

### Go builder

#### Support private repos

Support for private repositories was fixed. If using a private repository you must specify the `private-repository` input field as the repository name will be made public in the public Rekor transparency log.

Please add the following to your workflows if you opt into allowing repository names to be recorded in the public Rekor transparency log.

```yaml
with:
  private-repository: true
```

See #823

## New Contributors

- @sethmlarson made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/758
- @yunginnanet made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/776
- @diogoteles08 made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/957

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.2.0...v1.2.1

# v1.2.0

**DO NOT USE THIS RELEASE. This version will no longer work and is not supported due to errors described in #942. Please upgrade to [v1.2.2](https://github.com/slsa-framework/slsa-github-generator/releases/tag/v1.2.2) or later.**

## What's Changed

### Generic generator

The highlight of this release is a new re-usable workflow called the "Generic generator". It lets users build artifacts on their own and generate a provenance that satisfies SLSA provenance 3 requirement. It's perfect to get started with SLSA with minimal changes to an existing build workflow. To use it, check the [README.md](https://github.com/slsa-framework/slsa-github-generator/blob/main/internal/builders/generic/README.md)!

### Go builder

No changes.

## New Contributors

- @naveensrinivasan made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/352
- @renovate-bot made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/401
- @rarkins made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/489
- @developer-guy made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/497
- @loosebazooka made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/573

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.1.1...v1.2.0

# v1.1.1

## What's Changed

- Improve documentation
- Fix filename issue when resolving it with variables
- Add support for environment variables in artifact filename

## New Contributors

- @joshuagl made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/199
- @mihaimaruseac made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/202
- @MarkLodato made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/312
- @chipzoller made their first contribution in https://github.com/slsa-framework/slsa-github-generator/pull/354

## Full Changelog

https://github.com/slsa-framework/slsa-github-generator/compare/v1.0.0...v1.1.1

# v1.0.0

## What's Changed

This is the first official release of the generator. The first builder we are releasing is for Golang projects.
To learn how to use it, see [./README.md#golang-projects](https://github.com/slsa-framework/slsa-github-generator#golang-projects)

## Contributors

@asraa @ianlewis @MarkLodato @joshuagl @laurentsimon