Web of trust exploration
========================


Development
-----------

In order to set up a development environment, create a conda environment with
the required packages using the included environment file:

```
conda env create -f=environment.yml
```

Activate the environment, and add the repository directory to Python's path with
`conda develop`:

```
source activate wot-dev
conda develop .
```

Build the extension module in-place (this will need to be re-run if any changes
to `wot/_gpgme.c` are made):

```
python setup.py build_ext --inplace
```


Running tests
-------------

Execute the normal tests with:

```
py.test --pyargs daal
```

There are some tests for the initialisation code which must be run separately,
because there is no way to unload the C extension. To run the tests of the
initialisation code, execute py.test from the `extern_tests` folder:

```
cd extern_tests
py.test
```


Debugging
---------

In the case of issues coming from the extension module (e.g. exceptions thrown
reporting errors within a specific GPGME function), it can be helpful to turn on
debugging, which provides a lot of information about what the GPGME library is
doing and can help to trace the source of the issue. Turn this on with:

```
export GPGME_DEBUG=9
```

and then execute the problematic code as normal. Debugging output is sent to
stdout.
