# prisontest client

download the game from [releases](https://github.com/prisontest/prisontest-client/releases).
source code and build logs stay in the private source repository.

## requesting a release

configure these actions secrets in this repository:

- `SOURCE_REPOSITORY`: the private source repository, as `owner/repository`.
- `SOURCE_BUILD_TOKEN`: a fine-grained token restricted to that private repository
  with **Actions: read and write** access.

in the private source repository, install the native `prisoncpp.yml` workflow
that accepts a `release_tag` dispatch input. add `RELEASES_TOKEN` there, restricted
to this public repository with **Contents: read and write** access.

run **request client release** from the actions tab. enter a version such as
`v0.1.0` and a private source branch or tag, normally `main`. this workflow only
queues the private build. its successful completion does not mean the packages
have finished building; the private run publishes them after its checks pass.

this repository intentionally contains no game source or `VERSION` file.
do not copy the native build workflow here. the public workflow needs no checkout
and does not run on pushes, so publishing a release cannot start another build.
