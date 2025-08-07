[![Package version](https://img.shields.io/pypi/v/absl-py)](https://pypi.org/project/absl-py)
[![Supported Python versions](https://img.shields.io/pypi/pyversions/absl-py.svg?style=flat-square)](https://pypi.org/project/absl-py)
[![License](https://img.shields.io/github/license/abseil/abseil-py)](https://github.com/abseil/abseil-py/blob/main/LICENSE)
[![Build Status](https://github.com/abseil/abseil-py/actions/workflows/test.yml/badge.svg?branch=main)](https://github.com/abseil/abseil-py/actions)
[![Overall downloads](https://pepy.tech/badge/absl-py)](https://pepy.tech/project/absl-py)
[![Last month downloads](https://pepy.tech/badge/absl-py/month)](https://pepy.tech/project/absl-py)

# Abseil Python Common Libraries (Custom Fork)

> **Fork Notice**: This is a custom fork of [abseil/abseil-py](https://github.com/abseil/abseil-py) with modified log file naming.

## Custom Modifications

### Log File Extension Fix
- **Issue**: Original Abseil creates log files with non-standard naming: `app.hostname.user.log.INFO.timestamp.pid`
- **Fix**: Modified to append `.log` extension: `app.hostname.user.log.INFO.timestamp.pid.log`
- **File**: `absl/logging/__init__.py:900` - Added `.log` to basename format string

### Keeping Up with Upstream Updates

When Google releases new versions of abseil-py:

```bash
# 1. Fetch latest from upstream
git fetch upstream

# 2. Rebase your changes
git rebase upstream/main

# 3. If conflicts occur, apply the patch:
git apply add-log-extension.patch
```

**Patch file creation** (run once):
```bash
git format-patch -1 HEAD --stdout > add-log-extension.patch
```

### Installation
```bash
pip install git+https://github.com/matteolavaggi/abseil-py.git
```

---

# Original README

This repository is a collection of Python library code for building Python
applications. The code is collected from Google's own Python code base, and has
been extensively tested and used in production.

## Features

* Simple application startup
* Distributed commandline flags system
* Custom logging module with additional features
* Testing utilities

## Getting Started

### Installation

To install the package, simply run:

```bash
pip install absl-py
```

Or install from source:

```bash
pip install .
```

### Running Tests

To run Abseil tests, you can clone the git repo and run
[bazel](https://bazel.build/):

```bash
git clone https://github.com/abseil/abseil-py.git
cd abseil-py
bazel test absl/...
```

Please also validate the type annotations against the latest mypy:

```bash
pip install mypy
mypy absl
```

### Example Code

Please refer to
[smoke_tests/sample_app.py](https://github.com/abseil/abseil-py/blob/main/smoke_tests/sample_app.py)
as an example to get started.

## Documentation

See the [Abseil Python Developer Guide](https://abseil.io/docs/python/).

## Future Releases

The current repository includes an initial set of libraries for early adoption.
More components and interoperability with Abseil C++ Common Libraries
will come in future releases.

## License

The Abseil Python library is licensed under the terms of the Apache
license. See [LICENSE](LICENSE) for more information.
