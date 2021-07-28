# setup-meteor

This is a clone of https://github.com/meteorengineer/setup-meteor with updated npm packages, the latest github checkout version and node version matching the latest meteor release.

This action sets up meteor environment for use in actions.

# Usage

See [action.yml](action.yml)

Basic:

```yaml
steps:
  - uses: actions/checkout@v2
  - uses: meteorengineer/setup-meteor@v2
    with:
      meteor-release: "2.3.2"
  - run: meteor npm install
  - run: meteor npm test
```

Matrix Testing:

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        meteor: ["2.2", "2.3.2"]
    name: Meteor ${{ matrix.meteor }} sample
    steps:
      - uses: actions/checkout@v2
      - name: Setup meteor
        uses: johnwils/setup-meteor@v2
        with:
          meteor-release: ${{ matrix.meteor }}
      - run: meteor npm install
      - run: meteor npm test
```

# License

The scripts and documentation in this project are released under the [MIT License](LICENSE)
