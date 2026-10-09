# pin-maven-version

A Bash-based GitHub Action that downloads a specific Apache Maven version,
extracts it into runner temporary storage, and adds its `bin` directory to
`PATH` for subsequent steps.

## Usage

```yaml
steps:
  - uses: actions/setup-java@v4
    with:
      distribution: temurin
      java-version: '17'

  - uses: DMBeerman/pin-maven-version@main
    with:
      version: '3.9.9'

  - name: Check Maven version
    run: mvn --version
```

The required `version` input must identify a published Apache Maven binary
release on Maven Central. The runner must provide Bash, `curl`, and `tar`.
Java must be installed separately, with a version supported by the selected
Maven release. Downloads or extraction failures fail the action without
updating `PATH`.