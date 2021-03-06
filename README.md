[![Build Status](https://travis-ci.org/danvk/webdiff.svg?branch=master)](https://travis-ci.org/danvk/webdiff)
git webdiff
===========

Two-column web-based git difftool.

Features include:
* Side-by-side (two column) diff view
* Runs in the browser of your choice on any platform.
* Syntax highlighting via highlight.js
* Step back and forth through multiple files in a single diff
* Rich support for image diffs

Installation
------------

    pip install webdiff

Usage
-----

Instead of running "git diff", run:

    git webdiff

You can also start webdiff via:

    git webdiff [args]

You can pass all the same arguments that you would to `git diff`, e.g.
`1234..5678` or `HEAD`.

`webdiff` can also be invoked directly to diff two directories or files:

    webdiff <left_dir> <right_dir>
    webdiff <left_file> <right_file>

You can also use `webdiff` to view GitHub pull requests:

    webdiff https://github.com/owner/repo/pull/123
    webdiff #123  # if you're in a git repo with a github remote

This will download the files relevant to the Pull Request and run `webdiff`.

Preview
----------

![Screenshot of webdiff in action](http://www.danvk.org/webdiff.png)

This shows a JavaScript file being diffed. A few things to note:
* Line deletions and per-character modifications.
* Long stretches of common lines are elided, but can be shown if desired.
* Syntax highlighting (via highlight.js)
* Keyboard shortcuts (j/k) for stepping through files in the diff.

Development
-----------

(from an activated virtualenv)

    pip install -r requirements.txt
    bower install
    ./webdiff/app.py testdata/dygraphsjs/{left,right}

or to launch in debug mode:

    ./test.sh $(pwd)/../testdata/webdiffdiff/{left,right}

(or any other directory in testdata)

To run the Python tests:

    nosetests

To run the JavaScript tests:

    python -m SimpleHTTPServer
    open tests/runner.html

To iterate on the PyPI package, run:

    # from outside the webdiff virtualenv:
    pip uninstall webdiff

    # from inside the webdiff virtualenv, adjust for current version
    python setup.py sdist
    mkdir /tmp/webdiff-test
    cp dist/webdiff-X.Y.Z.tar.gz /tmp/webdiff-test

    deactivate
    cd /tmp/webdiff-test
    pip install webdiff-X.Y.Z.tar.gz
