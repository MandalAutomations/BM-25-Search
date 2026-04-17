# Building and testing Python

Learn how to create a continuous integration (CI) workflow to build and test your Python project.

## Introduction

This guide shows you how to build, test, and publish a Python package.

GitHub-hosted runners have a tools cache with pre-installed software, which includes Python and PyPy. You don't have to install anything! For a full list of up-to-date software and the pre-installed versions of Python and PyPy, see [GitHub-hosted runners](/en/actions/using-github-hosted-runners/about-github-hosted-runners#supported-software).

## Prerequisites

You should be familiar with YAML and the syntax for GitHub Actions. For more information, see [Writing workflows](/en/actions/learn-github-actions).

We recommend that you have a basic understanding of Python, and pip. For more information, see:

* [Getting started with Python](https://www.python.org/about/gettingstarted/)
* [Pip package manager](https://pypi.org/project/pip/)

## Using a Python workflow template

To get started quickly, add a workflow template to the `.github/workflows` directory of your repository.

GitHub provides a workflow template for Python that should work if your repository already contains at least one `.py` file. The subsequent sections of this guide give examples of how you can customize this workflow template.

1. On GitHub, navigate to the main page of the repository.

2. Under your repository name, click **<svg version="1.1" width="16" height="16" viewBox="0 0 16 16" class="octicon octicon-play" aria-label="play" role="img"><path d="M8 0a8 8 0 1 1 0 16A8 8 0 0 1 8 0ZM1.5 8a6.5 6.5 0 1 0 13 0 6.5 6.5 0 0 0-13 0Zm4.879-2.773 4.264 2.559a.25.25 0 0 1 0 .428l-4.264 2.559A.25.25 0 0 1 6 10.559V5.442a.25.25 0 0 1 .379-.215Z"></path></svg> Actions**.

   ![Screenshot of the tabs for the "github/docs" repository. The "Actions" tab is highlighted with an orange outline.](/assets/images/help/repository/actions-tab-global-nav-update.png)

3. If you already have a workflow in your repository, click **New workflow**.

4. The "Choose a workflow" page shows a selection of recommended workflow templates. Search for "Python application".

5. On the "Python application" workflow, click **Configure**.

6. Edit the workflow as required. For example, change the Python version.

7. Click **Commit changes**.

   The `python-app.yml` workflow file is added to the `.github/workflows` directory of your repository.

## Specifying a Python version

To use a pre-installed version of Python or PyPy on a GitHub-hosted runner, use the `setup-python` action. This action finds a specific version of Python or PyPy from the tools cache on each runner and adds the necessary binaries to `PATH`, which persists for the rest of the job. If a specific version of Python is not pre-installed in the tools cache, the `setup-python` action will download and set up the appropriate version from the [`python-versions`](https://github.com/actions/python-versions) repository.

Using the `setup-python` action is the recommended way of using Python with GitHub Actions because it ensures consistent behavior across different runners and different versions of Python. If you are using a self-hosted runner, you must install Python and add it to `PATH`. For more information, see the [`setup-python` action](https://github.com/marketplace/actions/setup-python).

The table below describes the locations for the tools cache in each GitHub-hosted runner.

<div class="ghd-tool rowheaders">

|                          | Ubuntu                          | Mac                                      | Windows                               |
| ------------------------ | ------------------------------- | ---------------------------------------- | ------------------------------------- |
| **Tool Cache Directory** | `/opt/hostedtoolcache/*`        | `/Users/runner/hostedtoolcache/*`        | `C:\hostedtoolcache\windows\*`        |
| **Python Tool Cache**    | `/opt/hostedtoolcache/Python/*` | `/Users/runner/hostedtoolcache/Python/*` | `C:\hostedtoolcache\windows\Python\*` |
| **PyPy Tool Cache**      | `/opt/hostedtoolcache/PyPy/*`   | `/Users/runner/hostedtoolcache/PyPy/*`   | `C:\hostedtoolcache\windows\PyPy\*`   |

</div>

If you are using a self-hosted runner, you can configure the runner to use the `setup-python` action to manage your dependencies. For more information, see [using setup-python with a self-hosted runner](https://github.com/actions/setup-python#using-setup-python-with-a-self-hosted-runner) in the `setup-python` README.

GitHub supports semantic versioning syntax. For more information, see [Using semantic versioning](https://docs.npmjs.com/about-semantic-versioning#using-semantic-versioning-to-specify-update-types-your-package-can-accept) and the [Semantic versioning specification](https://semver.org/).

### Using multiple Python versions

The following example uses a matrix for the job to set up multiple Python versions. For more information, see [Running variations of jobs in a workflow](/en/actions/using-jobs/using-a-matrix-for-your-jobs).

```yaml copy
name: Python package

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: ["pypy3.10", "3.9", "3.10", "3.11", "3.12", "3.13"]

    steps:
      - uses: actions/checkout@v5
      - name: Set up Python ${{ matrix.python-version }}
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
      # You can test your matrix by printing the current Python version
      - name: Display Python version
        run: python -c "import sys; print(sys.version)"
```

### Using a specific Python version

You can configure a specific version of Python. For example, 3.12. Alternatively, you can use semantic version syntax to get the latest minor release. This example uses the latest minor release of Python 3.

```yaml copy
name: Python package

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v5
      - name: Set up Python
        # This is the version of the action for setting up Python, not the Python version.
        uses: actions/setup-python@v5
        with:
          # Semantic version range syntax or exact version of a Python version
          python-version: '3.x'
          # Optional - x64 or x86 architecture, defaults to x64
          architecture: 'x64'
      # You can test your matrix by printing the current Python version
      - name: Display Python version
        run: python -c "import sys; print(sys.version)"
```

### Excluding a version

If you specify a version of Python that is not available, `setup-python` fails with an error such as: `##[error]Version 3.7 with arch x64 not found`. The error message includes the available versions.

You can also use the `exclude` keyword in your workflow if there is a configuration of Python that you do not wish to run. For more information, see [Workflow syntax for GitHub Actions](/en/actions/using-workflows/workflow-syntax-for-github-actions#jobsjob_idstrategy).

```yaml copy
name: Python package

on: [push]

jobs:
  build:

    runs-on: ${{ matrix.os }}
    strategy:
      matrix:
        os: [ubuntu-latest, macos-latest, windows-latest]
        python-version: ["3.9", "3.11", "3.13", "pypy3.10"]
        exclude:
          - os: macos-latest
            python-version: "3.11"
          - os: windows-latest
            python-version: "3.11"
```

### Using the default Python version

We recommend using `setup-python` to configure the version of Python used in your workflows because it helps make your dependencies explicit. If you don't use `setup-python`, the default version of Python set in `PATH` is used in any shell when you call `python`. The default version of Python varies between GitHub-hosted runners, which may cause unexpected changes or use an older version than expected.

| GitHub-hosted runner | Description                                                                                                                                                                                                                                                                                                                     |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Ubuntu               | Ubuntu runners have multiple versions of system Python installed under `/usr/bin/python` and `/usr/bin/python3`. The Python versions that come packaged with Ubuntu are in addition to the versions that GitHub installs in the tools cache.                                                                                    |
| Windows              | Excluding the versions of Python that are in the tools cache, Windows does not ship with an equivalent version of system Python. To maintain consistent behavior with other runners and to allow Python to be used out-of-the-box without the `setup-python` action, GitHub adds a few versions from the tools cache to `PATH`. |
| macOS                | The macOS runners have more than one version of system Python installed, in addition to the versions that are part of the tools cache. The system Python versions are located in the `/usr/local/Cellar/python/*` directory.                                                                                                    |

## Installing dependencies

GitHub-hosted runners have the pip package manager installed. You can use pip to install dependencies from the PyPI package registry before building and testing your code. For example, the YAML below installs or upgrades the `pip` package installer and the `setuptools` and `wheel` packages.

You can also cache dependencies to speed up your workflow. For more information, see [Dependency caching reference](/en/actions/using-workflows/caching-dependencies-to-speed-up-workflows).

```yaml copy
steps:
- uses: actions/checkout@v5
- name: Set up Python
  uses: actions/setup-python@v5
  with:
    python-version: '3.x'
- name: Install dependencies
  run: python -m pip install --upgrade pip setuptools wheel
```

### Requirements file

After you update `pip`, a typical next step is to install dependencies from `requirements.txt`. For more information, see [pip](https://pip.pypa.io/en/stable/cli/pip_install/#example-requirements-file).

```yaml copy
steps:
- uses: actions/checkout@v5
- name: Set up Python
  uses: actions/setup-python@v5
  with:
    python-version: '3.x'
- name: Install dependencies
  run: |
    python -m pip install --upgrade pip
    pip install -r requirements.txt
```

### Caching Dependencies

You can cache and restore the dependencies using the [`setup-python` action](https://github.com/actions/setup-python).

The following example caches dependencies for pip.

```yaml copy
steps:
- uses: actions/checkout@v5
- uses: actions/setup-python@v5
  with:
    python-version: '3.12'
    cache: 'pip'
- run: pip install -r requirements.txt
- run: pip test
```

By default, the `setup-python` action searches for the dependency file (`requirements.txt` for pip, `Pipfile.lock` for pipenv or `poetry.lock` for poetry) in the whole repository. For more information, see [Caching packages dependencies](https://github.com/actions/setup-python#caching-packages-dependencies) in the `setup-python` README.

If you have a custom requirement or need finer controls for caching, you can use the [`cache` action](https://github.com/marketplace/actions/cache). Pip caches dependencies in different locations, depending on the operating system of the runner. The path you'll need to cache may differ from the Ubuntu example above, depending on the operating system you use. For more information, see [Python caching examples](https://github.com/actions/cache/blob/main/examples.md#python---pip) in the `cache` action repository.

## Testing your code

You can use the same commands that you use locally to build and test your code.

### Testing with pytest and pytest-cov

This example installs or upgrades `pytest` and `pytest-cov`. Tests are then run and output in JUnit format while code coverage results are output in Cobertura. For more information, see [JUnit](https://junit.org/junit5/) and [Cobertura](https://cobertura.github.io/cobertura/).

```yaml copy
steps:
- uses: actions/checkout@v5
- name: Set up Python
  uses: actions/setup-python@v5
  with:
    python-version: '3.x'
- name: Install dependencies
  run: |
    python -m pip install --upgrade pip
    pip install -r requirements.txt
- name: Test with pytest
  run: |
    pip install pytest pytest-cov
    pytest tests.py --doctest-modules --junitxml=junit/test-results.xml --cov=com --cov-report=xml --cov-report=html
```

### Using Ruff to lint and/or format code

The following example installs or upgrades `ruff` and uses it to lint all files. For more information, see [Ruff](https://docs.astral.sh/ruff).

```yaml copy
steps:
- uses: actions/checkout@v5
- name: Set up Python
  uses: actions/setup-python@v5
  with:
    python-version: '3.x'
- name: Install the code linting and formatting tool Ruff
  run: pipx install ruff
- name: Lint code with Ruff
  run: ruff check --output-format=github --target-version=py39
- name: Check code formatting with Ruff
  run: ruff format --diff --target-version=py39
  continue-on-error: true
```

The formatting step has `continue-on-error: true` set. This will keep the workflow from failing if the formatting step doesn't succeed. Once you've addressed all of the formatting errors, you can remove this option so the workflow will catch new issues.

### Running tests with tox

With GitHub Actions, you can run tests with tox and spread the work across multiple jobs. You'll need to invoke tox using the `-e py` option to choose the version of Python in your `PATH`, rather than specifying a specific version. For more information, see [tox](https://tox.readthedocs.io/en/latest/).

```yaml copy
name: Python package

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest
    strategy:
      matrix:
        python: ["3.9", "3.11", "3.13"]

    steps:
      - uses: actions/checkout@v5
      - name: Setup Python
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python }}
      - name: Install tox and any other packages
        run: pip install tox
      - name: Run tox
        # Run tox using the version of Python in `PATH`
        run: tox -e py
```

## Packaging workflow data as artifacts

You can upload artifacts to view after a workflow completes. For example, you may need to save log files, core dumps, test results, or screenshots. For more information, see [Store and share data with workflow artifacts](/en/actions/using-workflows/storing-workflow-data-as-artifacts).

The following example demonstrates how you can use the `upload-artifact` action to archive test results from running `pytest`. For more information, see the [`upload-artifact` action](https://github.com/actions/upload-artifact).

```yaml copy
name: Python package

on: [push]

jobs:
  build:

    runs-on: ubuntu-latest
    strategy:
      matrix:
        python-version: ["3.9", "3.10", "3.11", "3.12", "3.13"]

    steps:
      - uses: actions/checkout@v5
      - name: Setup Python # Set Python version
        uses: actions/setup-python@v5
        with:
          python-version: ${{ matrix.python-version }}
      # Install pip and pytest
      - name: Install dependencies
        run: |
          python -m pip install --upgrade pip
          pip install pytest
      - name: Test with pytest
        run: pytest tests.py --doctest-modules --junitxml=junit/test-results-${{ matrix.python-version }}.xml
      - name: Upload pytest test results
        uses: actions/upload-artifact@v4
        with:
          name: pytest-results-${{ matrix.python-version }}
          path: junit/test-results-${{ matrix.python-version }}.xml
        # Use always() to always run this step to publish test results when there are test failures
        if: ${{ always() }}
```

## Publishing to PyPI

You can configure your workflow to publish your Python package to PyPI once your CI tests pass. This section demonstrates how you can use GitHub Actions to upload your package to PyPI each time you publish a release. For more information, see [Managing releases in a repository](/en/repositories/releasing-projects-on-github/managing-releases-in-a-repository).

The example workflow below uses [Trusted Publishing](https://docs.pypi.org/trusted-publishers/) to authenticate with PyPI, eliminating the need for a manually configured API token.

```yaml copy
# This workflow uses actions that are not certified by GitHub.
# They are provided by a third-party and are governed by
# separate terms of service, privacy policy, and support
# documentation.

# GitHub recommends pinning actions to a commit SHA.
# To get a newer version, you will need to update the SHA.
# You can also reference a tag or branch, but the action may change without warning.

name: Upload Python Package

on:
  release:
    types: [published]

permissions:
  contents: read

jobs:
  release-build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v5

      - uses: actions/setup-python@v5
        with:
          python-version: "3.x"

      - name: Build release distributions
        run: |
          # NOTE: put your own distribution build steps here.
          python -m pip install build
          python -m build

      - name: Upload distributions
        uses: actions/upload-artifact@v4
        with:
          name: release-dists
          path: dist/

  pypi-publish:
    runs-on: ubuntu-latest

    needs:
      - release-build

    permissions:
      # IMPORTANT: this permission is mandatory for trusted publishing
      id-token: write

    # Dedicated environments with protections for publishing are strongly recommended.
    environment:
      name: pypi
      # OPTIONAL: uncomment and update to include your PyPI project URL in the deployment status:
      # url: https://pypi.org/p/YOURPROJECT

    steps:
      - name: Retrieve release distributions
        uses: actions/download-artifact@v5
        with:
          name: release-dists
          path: dist/

      - name: Publish release distributions to PyPI
        uses: pypa/gh-action-pypi-publish@6f7e8d9c0b1a2c3d4e5f6a7b8c9d0e1f2a3b4c5d
```

For more information about this workflow, including the PyPI settings
needed, see [Configuring OpenID Connect in PyPI](/en/actions/deployment/security-hardening-your-deployments/configuring-openid-connect-in-pypi).