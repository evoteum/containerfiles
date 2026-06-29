[//]: # (STANDARD README)
[//]: # (https://github.com/RichardLitt/standard-readme)
[//]: # (----------------------------------------------)
[//]: # (Uncomment optional sections as required)
[//]: # (----------------------------------------------)

[//]: # (Title)
[//]: # (Match repository name)
[//]: # (REQUIRED)

# containerfiles

[//]: # (Banner)
[//]: # (OPTIONAL)
[//]: # (Must not have its own title)
[//]: # (Must link to local image in current repository)


[//]: # (Badges)
[//]: # (OPTIONAL)
[//]: # (Must not have its own title)


[//]: # (Short description)
[//]: # (REQUIRED)
[//]: # (An overview of the intentions of this repo)
[//]: # (Must not have its own title)
[//]: # (Must be less than 120 characters)
[//]: # (Must match GitHub's description)

Reusable Containerfiles

[//]: # (Long Description)
[//]: # (OPTIONAL)
[//]: # (Must not have its own title)
[//]: # (A detailed description of the repo)

Reusable Containerfiles for building Go, Python, and HTML (nginx) container images
across the Evoteum estate. Each Containerfile accepts build arguments so the same base
definition works for any project of that language type.


[//]: # (Keep this note to help people understand how to configure this repo.)
The configuration of this repo is managed by OpenTofu in
[estate-repos](https://github.com/evoteum/estate-repos).

## Table of Contents

[//]: # (REQUIRED)
[//]: # (TOCGEN_TABLE_OF_CONTENTS_START)

[//]: # (Table of contents will be automatically generated and inserted here.)

[//]: # (TOCGEN_TABLE_OF_CONTENTS_END)



[//]: # (## Security)
[//]: # (OPTIONAL)
[//]: # (May go here if it is important to highlight security concerns.)



[//]: # (## Background)
[//]: # (OPTIONAL)
[//]: # (Explain the motivation and abstract dependencies for this repo)

[//]: # (## Install)
[//]: # (OPTIONAL - documentation repo)

## Usage
[//]: # (REQUIRED)
[//]: # (Explain what the thing does. Use screenshots and/or videos.)

Containerfiles are consumed automatically by the `container-build-and-push` reusable workflow in [estate-reusable-workflows](https://github.com/evoteum/estate-reusable-workflows). The workflow selects the appropriate Containerfile based on the `REPOSITORY_LANGUAGE` variable set for each repo by [estate-repos](https://github.com/evoteum/estate-repos).

### Available Containerfiles

| Language | Base image                           | Notes                                                                |
|----------|--------------------------------------|----------------------------------------------------------------------|
| `go`     | `golang:${LANGUAGE_VERSION}-alpine`  | Multi-stage build; produces a minimal Alpine runtime image           |
| `html`   | `nginxinc/nginx-unprivileged:alpine` | Serves static files via nginx; expects an `nginx.conf` in the source |
| `python` | `python:${LANGUAGE_VERSION}`         | Installs from `requirements.txt`; entrypoint is `main.py`            |

### Build arguments

Each Containerfile accepts a `LANGUAGE_VERSION` build argument, set automatically from the `REPOSITORY_LANGUAGE_VERSION` variable in the target repository.



[//]: # (Extra sections)
[//]: # (OPTIONAL)
[//]: # (This should not be called "Extra Sections".)
[//]: # (This is a space for ≥0 sections to be included,)
[//]: # (each of which must have their own titles.)

## Why "Containerfiles" and not "Dockerfiles"

`Dockerfile` is a Docker-specific name for what is actually an OCI-standard build
format. Tools like Podman and Buildah use the same syntax but use the name
`Containerfile` to reflect that the format is not Docker-specific. We follow that
convention here; the files are identical in syntax, but the name accurately reflects
that they are not tied to Docker.

## A better approach

[Cloud Native Buildpacks](https://buildpacks.io/) are a superior alternative to
centralised Containerfiles. They automatically detect the language and build your
application without requiring a hand-maintained Containerfile per language. If you are
considering adopting this pattern, buildpacks should be evaluated before extending this
repository further. We intend to migrate to Cloud Native Buildpacks asap. 

[//]: # (## API)
[//]: # (OPTIONAL)
[//]: # (Describe exported functions and objects)



[//]: # (## Maintainers)
[//]: # (OPTIONAL)
[//]: # (List maintainers for this repository)
[//]: # (along with one way of contacting them - GitHub link or email.)



[//]: # (## Thanks)
[//]: # (OPTIONAL)
[//]: # (State anyone or anything that significantly)
[//]: # (helped with the development of this project)



## Contributing
[//]: # (REQUIRED)
If you need any help, please log an issue and one of our team will get back to you.

PRs are welcome.


## License
[//]: # (REQUIRED)

All our code is licenced under the AGPL-3.0. See [LICENSE](LICENSE) for more information.
