=========
Changelog
=========


7.0.1 (2025-07-24)
------------------

* hit PyPI project size limit. triggering re-upload to fix missing sdist in ``7.0.0`` release.
* deleted all PyPI releases up to version ``3.4.2`` (last version supporting python 2.7) to free up project space



7.0.0 (2025-07-21)
------------------

* Simplified API for end-users, reducing redundant code
* Added global functions that use a shared ``TimezoneFinder`` instance:
    * ``timezone_at``
    * ``timezone_at_land``
    * ``unique_timezone_at``
    * ``certain_timezone_at``
    * ``get_geometry``

* Documented usage and warned about thread safety considerations for global functions
* Updated command line interface to use global functions where appropriate
* breaking API Changes: clarified naming. renamed "boundary" to "bbox". renamed "polygon" to "boundary". boundaries (the outer polygon defining part of a timezone) and holes are both polygons so hence the name "polygon" is ambiguous.


6.6.3 (2025-07-21)
------------------

* when ``in_memory=True``, all polygon ``numpy`` arrays are constructed once during startup rather than repeatedly on demand. This should significantly improve performance for applications that make frequent polygons queries.
* Created a ``coord_accessors.py`` module for abstracting access to polygon coordinates, allowing for both in-memory and file-based access.
* added auto-generated data report to the documentation. thanks to `ARYAN RAJ <https://github.com/nikkhilaaryan>`__ for the PR.



6.6.2 (2025-07-19)
------------------

* hotfix missing `hole_registry.json` in the distributions
* added integration tests in CI/CD. Thanks to `theirix <https://github.com/theirix>`__


6.6.1 (2025-07-18)
------------------

* hotfix missing `flatbuf` module in the distributions
* added tests for checking the content of the distributions



6.6.0 (2025-07-17)
------------------

* major internal refactoring without breaking API changes. improvements for performance and code quality
* use `flatbuffer` binary files for storing the polygon coordinate data and the shorcuts (spatial h3 index) in binary format. removed any custom code for reading and writing binary files (e.g. seek operations)
* documented the binary format in the documentation
* grouping all data files into a single "data" folder
* added a new class PolygonArray to abstract away handling binary data of multiple polygons
* separate binary data storage folders for polygon boundaries and holes. handling both with the PolygonArray class
* parameterised location tests
* improved CLI code quality suppressing any output. added nicer output in verbose mode
* dropped support for python 3.8 (reached the end of life). thanks to `ARYAN RAJ <https://github.com/nikkhilaaryan>`__ for the PR.
* added support for official for python 3.12
* added usage example scripts
* switched from `poetry` to `uv` for dependency management and packaging. Thanks to `theirix <https://github.com/theirix>`__


6.5.9 (2025-03-25)
------------------

* updated the timezone boundary data to version `2025b <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2025b>`__. Thanks to `WestonReed <https://github.com/WestonReed>`__



6.5.8 (2025-01-21)
------------------

* updated the data to `2025a <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2025a>`__
* internal: updated ``file_converter.py`` for ``h3>=4``


6.5.7 (2024-12-02)
------------------

* improved error handling to catch ``ValueError: not enough values to unpack`` (`Issue #209 <https://github.com/jannikmi/timezonefinder/issues/209>`__)


6.5.6 (2024-12-02)
------------------

* add musllinux Wheels for Linux. Thanks to `Pxli9130 <https://github.com/Pxli9130>`__


6.5.5 (2024-11-20)
------------------

* using ``setuptools`` only as a build dependency. Thanks to `Kristian Sloth Lauszus <https://github.com/Lauszus>`__


6.5.4 (2024-10-22)
------------------

* using the dependency ``h3>4``. Thanks to `Greg Meyer <https://github.com/gmmeyer>`__


6.5.3 (2024-09-16)
------------------

* updated the data to `2024b <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2024b>`__.
* refactored C lang point in polygon utils

6.5.2 (2024-06-17)
------------------

* added support for ``numpy>=2.0`` (fixes issue #234)


6.5.1 (2024-06-14)
------------------

* added support for ``cibuildwheel``: publish wheels including the native C extension. GHA CI/CD pipeline creates sdist (no binaries inside) and a bunch of binary wheels with a prebuilt clang-pip extension for each python version. Thanks to `theirix <https://github.com/theirix>`__



6.5.0 (2024-03-14)
------------------

* updated the data to `2024a <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2024a>`__.

internal:

* use ruff linter in pre-commit hook
* make dependency specifications less strict


6.4.1 (2024-02-08)
------------------

* added official support for python 3.8 again, by specifying numba as multiple constraint dependency


internal:

* added unit tests for polygon boundary binary reading


6.4.0 (2024-02-02)
------------------

* added python 3.12 support (supported by numba since release 0.59.0), Closes #208
* dropped official support for python 3.8, because the optional dependency numba requires python 3.9. this package might still work with python 3.8, but it is not tested anymore.


6.3.0 (2024-02-01)
------------------

* updated the data to `2023d <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2023d>`__.

internal:

* added docstrings. Thanks to `Tyler Huntley <https://github.com/Ty1776>`__
* automatically skip GitHub actions publishing when the version already exists. useful for minor improvements without publishing a version. build would always fail otherwise
* enable tests for python 3.11 with numba
* enable tests for python 3.12
* added tests for generating the documentation
* use poetry dependency group specification (closing #199)


6.2.0 (2023-03-26)
------------------

* updated the data to `2023b <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2023b>`__.


6.1.10 (2023-03-22)
-------------------

* added a `pytz` extra for easily maintaining compatibility
* improved documentation

6.1.9 (2022-12-06)
------------------

* updated the data to `2022g <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2022g>`__.


6.1.8 (2022-11-25)
------------------

* pumped ``h3`` dependency to ``>=3.7.6,<4`` to support python 3.11 (FIX #170)
* added python 3.11 tests (not yet supporting numba)


6.1.7 (2022-11-20)
------------------

* updated the data to `2022f <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2022f>`__.
* pinning dependencies more strictly

6.1.6 (2022-10-30)
------------------

* updated the data to `2022d <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2022d>`__.


6.1.5 (2022-10-25)
------------------

* updated the data to `2022b <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2022b>`__.
* logging build failures with warnings


6.1.4 (2022-10-23)
------------------

* more permissive optional ``Numba`` dependency specification (FIX #162, impossible using latest numpy version)
* made all dependency specifications more permissive following the same rationale


6.1.3 (2022-09-23)
------------------

* bugfix broken package build in the case of a broken ``cffi`` installation (GitHub issue #155). Skip build process if ``cffi`` fails. For performance reasons using the C extension should remain the default behavior. Hence the ``cffi`` dependency should not be optional.


6.1.2 (2022-09-13)
------------------

* bugfix potentially broken pip install due to a mismatch in ``cffi`` versions (GitHub issue #151)


6.1.1 (2022-08-18)
------------------

internals:

* minimized and cleaned up installation footprint (addresses GitHub Issue #151):
    * excluded script, changelog etc. files
    * included C extension into the "timezonefinder" package folder
* added initialisation speed benchmark


6.1.0 (2022-08-15)
------------------

* included point-in-polygon implementation in C
* included build script to (optionally) build C point-in-polygon extension automatically during installation
* added ``cffi`` as a dependency to build and interact with the C extension
* improved initialisation speed: read timezone polygon id index (h3 mapping) with ``np.fromfile``
* improved CLI speed: construct TimezoneFinder() instances only on demand

internals:

* updated documentation: ``Numba`` installation is no longer recommended (it is a huge dependency and should be optional)
* clarified documentation: TimezoneFinder() instances should be reused
* added separate speed benchmark scripts for point in polygon algorithm implementations and the different timezone finding functions
* added separate section in the documentation for performance including speed benchmark results
* added checks if all timezone polygons are actually in use (appear in index) to the file conversion script
* added and improved utility functions as well as tests
* improved typing


6.0.2 (2022-07-08)
------------------

* bump numpy dependency version to ``1.22`` (vulnerability fix)
* officially supported python versions ``>=3.8,<3.11`` (due to numpy and numba constraints)
* packaging now completely based on pyproject.toml (poetry)


6.0.1 (2022-05-20)
------------------

* explicitly included ``py.typed`` in the package to allow mypy users to run static type checking


6.0.0 (2022-05-09)
------------------

breaking changes:

* new dependency: using `h3 <https://uber.github.io/h3-py/intro.html>`__ for indexing the timezone polygons to check ("shortcuts) instead of the previous own indexing implementation. technical details: storing all 41,162 hex cells at resolution 3 and the corresponding timezone polygons which appear in them in the ``shortcuts.bin`` (~500 KB).
* removed ``.closest_timezone_at()``: with the current data set with ocean zones in use, any point is included in some zone. it is therefore not meaningful to search for the closest boundary! Also the timezone polygons do NOT follow the shorelines. This makes the results of ``closest_timezone_at()`` somewhat less expressive. Maintaining the non-trivial distance computation algorithms is not really at the core responsibility of this package.
* officially only supporting ``python>=3.7`` (removed official support for ``python3.6``, since the ``numpy`` dependency did so)
* removed ``v`` from the github release/version tags

internals:

* updated the data to `2021c <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2021c>`__. please note that timezone polygons might be overlapping (cf. e.g. `timezone-boundary-builder/issue/105 <https://github.com/evansiroky/timezone-boundary-builder/issues/105>`__) and that hence a query coordinate can actually match multiple time zones. ``timezonefinder`` does currently NOT support such multiplicity and will always only return the first found match.
* shortcuts: sorting according to size of polygons (amount of coordinates) instead of the count of zone ids. useful as optimisation: smaller polygons will be checked first and can hence be "ruled-out" faster
* "most common": now meaning the zone with the largest polygons in the shortcut (last in the shortcut sorting). please note that this does not necessarily mean the most area in the shortcut is covered by this zone. the polygon size is just an easier to compute heuristic.
* officially supporting python versions >=3.7,<3.11 (like ``numba``)
* using poetry for dependency management
* using GitHub actions for CI instead of travis
* some minor typing improvements
* pre-commit hook improvements

In case you have criticism or feedback please reach out by creating an issue, discussion or PR on GitHub.


5.2.0 (2021-02-09)
------------------

* added function ``unique_timezone_at()`` (based on the request in issue #112). Allows querying for the unique zone within the corresponding shortcut.


5.1.1 (2021-02-03)
------------------

* BUGFIX: get_geometry() now also works for the last zone
* add get_geometry() tests
* black code style
* pre-commit checks

5.1.0 (2021-01-14)
------------------

* update the command line interface. the package can now directly be called with ``timezonefinder``
* added the new query functions to the command line interface (to match the online API)


5.0.0 (2020-12-23)
------------------

MAJOR CHANGES:

Due to multiple user requests the ocean timezones ("Etc/GMT+-XX") are now included in the data files per default. fix #88. Since ocean timezones span the whole globe, now every point lies within a timezone!

API changes:
* added ``timezone_at_land()``: replaces the previous ``timezone_at()`` and returns ``None`` in case of a matched ocean timezone.

* deprecated ``certain_timezone_at()``. only meaningful in the case of timezone data WITHOUT oceans. Has equal results as  ``timezone_at()``, but is more expensive to use.
* also looking a single closest timezone boundary with ``closest_timezone_at()`` is not really meaningful, since every point lies within a zone!
* refactored tests. new test cases for ocean timezones


4.5.0 (2020-11-06)
------------------

BUGFIX: handle output destination for data files correctly in file_converter.py (FIX #107)

* updated the data to `2020d <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2020d>`__
* disable a test case for an Uzbek enclave. tests fail at this coordinate, possibly a bug. issue filed here: https://github.com/evansiroky/timezone-boundary-builder/issues/94
* update parse_data.sh script to properly handle new data format


4.4.1 (2020-08-04)
------------------

BUGFIX: a longitude of 180 equals -180 (not 0.0 as previously implemented)


4.4.0 (2020-05-14)
------------------

* added new class TimezonefinderL for using JUST shortcuts (without timezone polygon data)
* therefore included the most common timezone of each shortcut stored in the binary file ``shortcuts_direct_id.bin``
* introduced typing
* included API documentation
* read hole registry directly from json, ``hole_poly_ids.bin`` not required any more
* added the ``parse_data.sh`` shell script for downloading the latest timezone data, also with oceans


improvements of file_converter.py:

* added command line arguments for specifying the input and output directories
* read binary names from ``global_settings.py``
* read data types from ``global_settings.py``
* use with statement for writing binaries
* automatically detect overflow for each data type in use
* cleanup code, remove redundancies, improve codestyle
* fixing #101: make imports work for local and remote execution




4.3.1 (2020-04-29)
------------------

* BUGFIX #99: include the correct timezone_names.json in build
* wheel specific for the supported python versions (3.6, 3.7, 3.8)

4.3.0 (2020-04-28)
------------------

* updated the data to `2020a <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2020a>`__
* added "extra" simplifying the installation of Numba
* added minimal required python version
* added minimal required version of the dependencies
* simplified and updated settings (e.g. reading current version from file)
* also testing python 3.8 now
* loading version from file

4.2.0 (2019-12-15)
------------------

* added option to specify the location of the binary data files to use. making it possible to easily point to own compiled data. also load timezone names json from this location
* make timezone names a class attribute (instead of a global variable)
* simplify code for opening and closing multiple binary files
* added tests for a specified path to the data
* testing multiple python3 versions automatically
* pinned new requirements
* importlib_resources removed from the dependencies
* added a documentation at: https://timezonefinder.readthedocs.io/en/latest/
* added contribution guidelines


4.1.0 (2019-07-07)
------------------

* updated the data to `2019b <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2019b>`__
* added description of using vectorized input in readme



4.0.3 (2019-06-23)
------------------

* clarification of readme: referenced latest `timezonefinderL` release, better rst headlines, updated shield.io banner syntax
* clarification of speedup times (exponential notation)
* removed `six` and py2 dependency from tests
* minor updates to publishing routine
* minor improvement in timezone_at(): conversion coordinates to int later only when required


4.0.2 (2019-04-01)
------------------

* updated the data to `2019a <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2019a>`__


4.0.1 (2019-03-12)
------------------

* BUGFIX: fixing #77 (missing dependency in setup.py)


4.0.0 (2019-03-12)
------------------

* ATTENTION: Dropped Python2 support (#72)! `six` dependency no longer required.
* BUGFIX: fixing #74 (broken py3 with numba support)
* added `in_memory`-mode (adapted unit tests to test both modes, added speed tests and explanation to readme)
* use of timeit in speed tests for more accurate results
* dropped use of kwargs_only decorator (can be implemented directly with python3)

3.4.2 (2019-01-15)
------------------

* BUGFIX: fixing #70 (broken py2.7 with numba support)
* added automatic tox tests for py2.7 py3 environments with numba installed
* fixed coverage report

3.4.1 (2019-01-13)
------------------

* added test cases for the Numba helpers (#55)
* added more polygon tests to test the function inside_polygon()
* added global data type definitions (format strings) to ``global_settings.py``
* removed tzwhere completely from the main tests (no comparison any more).
* removed code drafts for ahead of time compilation (#40)

3.4.0 (2019-01-06)
------------------

* updated the data to `2018i <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2018i>`__
* introduced ``global_settings.py`` to globally define settings and get rid of "magic numbers".


3.3.0 (2018-11-17)
------------------

* updated the data to `2018g <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2018g>`__



3.2.1 (2018-10-30)
------------------

* ATTENTION: the package ``importlib_resources`` is now required
* fixing automatic Conda build by exchanging ``pkg_resources.resource_stream`` with ``importlib_resources.open_binary``
* added tests for overflow in helpers.py/inside_polygon()


3.2.0 (2018-10-23)
------------------

* ATTENTION: the package `kwargs_only <https://github.com/adamchainz/kwargs-only>`__ is not a requirement any more!
* fixing #63 (kwargs_only not in conda) enabling automatic conda forge builds by directly providing the kwargs_only functionality again
* added example.py with the code examples from the readme
* fixing #62 (overflow happening because of using numpy.int32): forcing int64 type conversion



3.1.0 (2018-09-27)
------------------

* fixing typo in requirements.txt
* updated publishing routine: reminder to include all direct dependencies and to compile the requirements.txt with python 2 (pip-tools)


3.0.2 (2018-09-26)
------------------

* ATTENTION: the package `kwargs_only <https://github.com/adamchainz/kwargs-only>`__ is now required! This functionality has previously been implemented by the author directly within this package, but some code features got deprecated.
* updated build/testing/publishing routine
* fixing issue #61 (six dependency not listed in setup.py)
* no more default arguments for timezone_at() and certain_timezone_at()
* no more comparison to (py-)tzwhere in the tests (test_it.py)
* updated requirements.txt (removed tzwhere and dependencies)
* prepared helpers_test.py for also testing helpers_numba.py
* exchanged deprecated inspect.getargspec() into .getfullargspec() in functional.py


3.0.1 (2018-05-30)
------------------

* fixing minor issue #58 (readme not rendering in pyPI)


3.0.0 (2018-05-17)
------------------

* ATTENTION: the package six is now required! (was necessary because of the new testing routine. improves compatibility standards)
* updated build/testing/publishing routine
* updated the data to `2018d <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2018d>`__
* fixing minor issue #52 (shortcuts being out of bounds for extreme coordinate values)
* the list of polygon ids in each shortcut is sorted after freq. of appearance of their zone id.
    this is critical for ruling out zones faster (as soon as just polygons of one zone are left this zone can be returned)
* using argparse package now for parsing the command line arguments
* added option of choosing between functions timezone_at() and certain_timezone_at() on the command line with flag -f
* the timezone names are now being stored in a readable JSON file
* adjusted the main test cases
* corrections and clarifications in the readme and code comments


2.1.2 (2017-11-20)
------------------

* bugfix: possibly uninitialized variable in closest_timezone_at()


2.1.1 (2017-11-20)
------------------

* updated the data to `2017c <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2017c>`__
* minor improvements in code style and readme
* include publishing routine script


2.1.0 (2017-05-19)
------------------

* updated the data to `2017a <https://github.com/evansiroky/timezone-boundary-builder/releases/tag/2017a>`__ (tz_world is not being maintained any more)
* the file_converter has been updated to parse the new format of .json files
* the new data is much bigger (based on OSM Data, +40MB). I am sorry for this but its still better than small outdated data!
* in case size and speed matter more you than actuality, you can still check out older versions of timezonefinder(L)
* the new timezone polygons are not limited to the coastlines, but they are including some large parts of the sea. This makes the results of closest_timezone_at() somewhat meaningless (as with timezonefinderL).
* the polygons can not be simplified much more and as a consequence timezonefinderL is not being updated any more.
* simplification functions (used for compiling the data for timezonefinderL) have been deleted from the file_converter
* the readme has been updated to inform about this major change
* some tests have been temporarily disabled (with tzwhere still using a very old version of tz_world, a comparison does not make too much sense atm)

2.0.1 (2017-04-08)
------------------

* added missing package data entries (2.0.0 didn't include all necessary .bin files)


2.0.0 (2017-04-07)
------------------

* ATTENTION: major change!: there is a second version of timezonefinder now: `timezonefinderL <https://github.com/jannikmi/timezonefinderL>`__. There the data has been simplified
    for increasing speed reducing data size. Around 56% of the coordinates of the timezone polygons have been deleted there. Around 60% of the polygons (mostly small islands) have been included in the simplified polygons.
    For any coordinate on landmass the results should stay the same, but accuracy at the shorelines is lost.
    This eradicates the usefulness of closest_timezone_at() and certain_timezone_at() but the main use case for this package (= determining the timezone of a point on landmass) is improved.
    In this repo timezonefinder will still be maintained with the detailed (unsimplified) data.
* file_converter.py has been complemented and modified to perform those simplifications
* introduction of new function get_geometry() for querying timezones for their geometric shape
* added shortcuts_unique_id.bin for instantly returning an id if the shortcut corresponding to the coords only contains polygons of one zone
* data is now stored in separate binaries for ease of debugging and readability
* polygons are stored sorted after their timezone id and size
* timezonefinder can now be called directly as a script (experimental with reduced functionality, cf. readme)
* optimisations on point in polygon algorithm
* small simplifications in the helper functions
* clarification of the readme
* clarification of the comments in the code
* referenced the new conda-feedstock in the readme
* referenced the new timezonefinder API/GUI



1.5.7 (2016-07-21)
------------------


* ATTENTION: API BREAK: all functions are now keyword-args only (to prevent lng lat mix-up errors)
* fixed a little bug with too many arguments in a @jit function
* clarified usage of the package in the readme
* prepared the usage of the ahead of time compilation functionality of Numba. It is not enabled yet.
* sorting the order of polygons to check in the order of how often their zones appear, gives a speed bonus (for closest_timezone_at)


1.5.6 (2016-06-16)
------------------

* using little endian encoding now
* introduced test for checking the proper functionality of the helper functions
* wrote tests for proximity algorithms
* improved proximity algorithms: introduced exact_computation, return_distances and force_evaluation functionality (s. Readme or documentation for more info)

1.5.5 (2016-06-03)
------------------

* using the newest version (2016d, May 2016) of the `tz world data`_
* holes in the polygons which are stored in the tz_world data are now correctly stored and handled
* rewrote the file_converter for storing the holes at the end of the timezone_data.bin
* added specific test cases for hole handling
* made some optimizations in the algorithms

1.5.4 (2016-04-26)
------------------

* using the newest version (2016b) of the `tz world data`_
* rewrote the file_converter for parsing a .json created from the tz_worlds .shp
* had to temporarily fix one polygon manually which had the invalid TZID: 'America/Monterey' (should be 'America/Monterrey')
* had to make tests less strict because tzwhere still used the old data at the time and some results were simply different now


1.5.3 (2016-04-23)
------------------

* using 32-bit ints for storing the polygons now (instead of 64-bit): I calculated that the minimum accuracy (at the equator) is 1cm with the encoding being used. Tests passed.
* Benefits: 18MB file instead of 35MB, another 10-30% speed boost (depending on your hardware)


1.5.2 (2016-04-20)
------------------

* added python 2.7.6 support: replaced strings in unpack (unsupported by python 2.7.6 or earlier) with byte strings
* timezone names are now loaded from a separate file for better modularity


1.5.1 (2016-04-18)
------------------

* added python 2.7.8+ support:
    Therefore I had to change the tests a little bit (some operations were not supported). This only affects output.
    I also had to replace one part of the algorithms to prevent overflow in Python 2.7


1.5.0 (2016-04-12)
------------------

* automatically using optimized algorithms now (when numba is installed)
* added TimezoneFinder.using_numba() function to check if the import worked


1.4.0 (2016-04-07)
------------------

* Added the ``file_converter.py`` to the repository: It converts the .csv from pytzwhere to another ``.csv`` and this one into the used ``.bin``.
    Especially the shortcut computation and the boundary storage in there save a lot of reading and computation time, when deciding which timezone the coordinates are in.
    It will help to keep the package up to date, even when the timezone data should change in the future.


    .. _tz world data: <http://efele.net/maps/tz/world/>
