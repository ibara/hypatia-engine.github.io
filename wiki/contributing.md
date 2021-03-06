---
title: Contributing to Hypatia
---

Want to get started contributing to Hypatia? Here's a few ways to help out, and chat to the other developers of the project!

## Contents
{:.no_toc}

* Table of Contents
{:toc}


## Tackle a "help wanted" issue

The Hypatia GitHub repository has a collection of issues that are marked as "help wanted". These issues are a good place to start jumping in to development of the engine.

The current "help wanted" issues are listed [over here](https://github.com/hypatia-engine/hypatia/labels/help%20wanted).

## Chat with the developers on Slack

The Hypatia developers all talk on Slack, a team communication platform. If you would like to join us and contribute ideas, or just chat with the team, you can join by sending Lillian an email, at [lillian.lynn.lemmer@gmail.com](mailto:lillian.lynn.lemmer@gmail.com).

## Guidelines for contributing

### Git flow

The general git flow of the project follows [A Successful git Branching Model](http://nvie.com/posts/a-successful-git-branching-model/). Please branch from the `develop` branch.

### Documentation rules

* Always use gender neutral pronouns in all documentation, including code comments, e.g., they, them, their.
* Use one space (not two) to separate sentences.
* Docstrings are in reStructuredText, all other documents are in Markdown.

### Python style guidelines

Hypatia is strict about the style of code.

* Aim for 100% test coverage, as seen through [coveralls.io](https://coveralls.io/r/lillian-lemmer/hypatia)
* Hypatia has a strict style code. PEP8 nonconforming code will generate errors on the [Travis CI account](https://travis-ci.org/hypatia-engine/hypatia)
* Code is also checked by [code climate](https://codeclimate.com/github/lillian-lemmer/hypatia)
* Use `test.sh` in the repo's root to test your code *before* committing your changes. The test script uses `pytest`, `pytest-cov`, and `pytest-pep8`.

The following statements must have a blank line above and below:

  * `return`
  * `break`
  * `continue`
  * `yield`
  * `raise`

Examples of what _must have a blank line above and below_:

```
if x == 2:

    continue

elif x == 3:

    return None

elif x == 4:
    x += 1
elif x == 6:

    break

elif x == 10:

    raise Exception('derp!')
```

The following must have a blank line above:

  * `except`: when the respective `try` block exceeds one line
  * `else`, `elif`: when the previous `else`, `elif`, or `if` block exceeded one line

Example of what _must have a blank line above_:

```
try:
    d = {}
    d['lol no such key']

except KeyError:
    print("what a horrible example")

if x == 3:
    x += 5
    y -= 3
    a = x - y

elif x == 5:
    x -= 4
elif x == 6:
    x += 8
    y -= 9

else:
    x = 5
```

#### Docstrings

Hypatia is strictest about _docstrings_. The docstring convention used is the Google docstring format. Here are some great references on that style:

* [Example Google docstrings](http://sphinxcontrib-napoleon.readthedocs.org/en/latest/example_google.html)
* [The official spec from Google](http://google.github.io/styleguide/pyguide.html)
* Use FOUR spaces to indent things in docstrings, NOT two!
* We use Sphinx to generate our API docs.
* Napoleon is a Sphinx module we use which parses Google-style docstrings. It'd be a good idea to read [the official Napoleon/Google docstring docs](http://sphinxcontrib-napoleon.readthedocs.org/en/latest/).

Docstrings are required for modules, functions, classes, and methods.

#### Doctests

We also use require doctests for all classes, methods, and functions. It is also required to run doctest if a module is being executed as main. Here are some relevant cherry-picked resources on the matter:

  * [Official Python guide on doctests](https://docs.python.org/2/library/doctest.html)
  * [A wonderful, more thorough guide on doctests](http://pymotw.com/2/doctest/)

Our doctests are verified by Travis CI. You can avoid embarassment by running the `test.sh` supplied in the repo to test your changes.

#### Creating tests

* Hypatia uses pytest for automated testing. To set up your Hypatia repository for testing, run the following:

  ```
  cd /path/to/hypatia-repository
  pip install -r requirements/testing.txt
  ```

  You can now run the tests by running `test.sh`.

* Reference `tests/test_tiles.py` for an example on how to structure your tests. See [official pytest usage examples](http://pytest.org/latest/example) for more generic samples. 
  * Avoid creating classes in your tests.
  * The following try/except block is needed:

    ```
        try:
            os.chdir('demo')
        except OSError:
            pass
    ```