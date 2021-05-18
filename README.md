# sample-action

The following workflow will run ./gradlew build using the wrapper from the repository on ubuntu, macos and windows. The only prerequisite is to have Java installed, you can define the version you need to run the build using the actions/setup-java action.

**Usage**
```
# .github/workflows/gradle-build.yml
name: Run Gradle on PR
on: pull_request
jobs:
  gradle:
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
    runs-on: ${{ matrix.os }}
    steps:
    - uses: actions/checkout@v2
    - uses: actions/setup-java@v1
      with:
        java-version: 11
    - uses: puredevops/sample-action@v1.2
      with:
        arguments: build
```
