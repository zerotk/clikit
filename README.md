[![PyPI](https://img.shields.io/pypi/v/zerotk.clikit.svg?style=flat-square)](https://pypi.python.org/pypi/zerotk.clikit)
[![Travis](https://img.shields.io/travis/zerotk/clikit.svg?style=flat-square)](https://travis-ci.org/zerotk/clikit)
[![Coveralls](https://img.shields.io/coveralls/zerotk/clikit.svg?style=flat-square)](https://coveralls.io/github/zerotk/clikit)

# zerotk.clikit

A modern Command Line Interface library, making use of techniques such as dependency injection to
create a solid foundation for command line utilities and applications development.

## Example

This is the hello world example with steroids.

```python
from zerotk.clikit.app import App
import sys

app = App('hello')

@app
def greeting(console_, person, cumpliment='Hello', exclamation=False):
    '''
    Greetings from clikit.

    :param person: Who to say it to.
    :param cumpliment: What to say.
    :param exclamation: Uses exclamatino point instead of a period.
    '''
    puntuation = '!' if exclamation else '.'
    console_.Print('%(cumpliment)s, %(person)s%(puntuation)s' % locals())

if __name__ == '__main__':
    sys.exit(app.Main())
```

We'll have:

```bash
$ hello.py

Usage:
    hello <subcommand> [options]

Commands:
    greeting   Greetings from clikit.

$ hello.py greeting
ERROR: Too few arguments.

Greetings from clikit.

Usage:
    greeting <person> [--cumpliment=Hello],[--exclamation]

Parameters:
    person   Who to say it to.

Options:
    --cumpliment   What to say. [default: Hello]
    --exclamation   Uses exclamatino point instead of a period.

$ hello.py greeting world
Hello, world.

$ hello.py greeting planet --cumpliment=Hi --exclamation
Hi, planet!
```
