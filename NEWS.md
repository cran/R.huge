# R.huge

## Version 0.10.0 [2023-06-24]

### Miscellaneous

 * Now importing `throw()` from **R.oo** instead of **R.methodsS3**,
   because the latter is deprecated and will soon be removed.
 
 * Coerced NEWS file to NEWS.md.

 * Update outdated or broken URLs in the documentation.
 

## Version 0.9.0 [2014-02-22]

### Significant Changes

 * Now declaring all S3 methods in NAMESPACE.


## Version 0.8.0 [2014-02-25]

### Bug Fixes

 * Now the package runs the garbage collector if unloaded in order to
   make sure `finalize()` is called on any deleted `AbstractFileArray`
   objects.

### Miscellaneous

 * Bumped package dependencies.


## Version 0.7.0 [2014-01-05]

### Significant Changes

 * Package no longer attaches **R.oo** - only imports it.

### Miscellaneous

 * Bumped package dependencies.


## Version 0.6.1 [2014-01-05]

### New Features

 * Now the `R.huge` `Package` object is also available when the
   package is only loaded (but not attached).

### Miscellaneous

 * Bumped package requirements and no-longer needed import statements
   from NAMESPACE.


## Version 0.6.0 [2013-09-21]

### Significant Changes

 * Now declaring all S3 methods in NAMESPACE.

### Miscellaneous

 * Package no longer utilizes `import()`, only
   `importFrom()`:s.

 * Removed fallback attachments of **R.utils** as these are
   no longer needed with **R.oo** (>= 1.15.1).

 * Cleaned out unnecessary `appendVarArgs()`.

 * Added another package system test.

 * For now, package attaches the **R.oo** package. This is needed due
   to what appears to be a bug in how **R.oo** finalizes `Object`:s
   assuming **R.oo** is/can be attached.  Until that is resolved, we
   make sure **R.oo** is attached.


## Version 0.5.1 [2013-08-02]

### Miscellaneous

 * Utilizing new `startupMessage()` of **R.oo**.


## Version 0.5.0 [2013-08-02]

### Significant Changes

 * Package no longer attaches/loads **R.utils** (only imports
   it). However, it will attach ("load") **R.utils** dynamically, when
   certain methods are called.


## Version 0.4.4 [2013-05-25]

### Miscellaneous

 * Minor speedup by replacing `rm()` calls with `NULL` assignments.


## Version 0.4.3 [2013-05-22]

### Miscellaneous

 * CRAN POLICY: Now all Rd `\usage{}` lines are at most 90 characters
   long.


## Version 0.4.2 [2012-10-16]

### Bug Fixes

 * No longer passing `...` to `NextMethod()`, cf. R-devel thread 'Do
   *not* pass '...' to `NextMethod()` - it'll do it for you; missing
   documentation, a bug or just me?' on Oct 16, 2012.


## Version 0.4.1 [2012-06-29]

### Miscellaneous

 * Updated package requirements.


## Version 0.4.0 [2012-04-12]

### Miscellaneous

 * Updated package requirements.

 * Package no longer call `.Internal()` functions.  This will cause a
   slowdown, because we now have to deal with overhead in functions
   such as `seek()`, `readBin()` and `writeBin()`.

 * Package no longer creates new generic functions for `as.vector()`
   and `as.matrix()` such that `R CMD check` no longer complaints.


## Version 0.3.0 [2011-07-23]

### Significant Changes

 * Added a namespace to the package, which will be more or less a
   requirement in the next major release of R.

### Bug Fixes

 * Recently R devel automatically adds a namespace to a package, if
   missing.  This caused some of the **PSCBS** examples to throw an
   exception related to incorrect dispatching of `cat()`.


## Version 0.2.2 [2011-02-01]

### Miscellaneous

 * Now using argument `nchars` (not `nchar`) when calling
   `readChar()`.


## Version 0.2.1 [2010-11-08]

### New Features

 * Now `[()` for `FileMatrix` explicitly specifies `origin="current"`
   in the call to `readBinFragment()`, which is an argument added in
   **R.utils** 1.5.7.

### Miscellaneous

 * Removed some defunct Rd aliases.


## Version 0.2.0 [2009-10-16]

### Miscellaneous

 * Some cleanup of Rd files to meet the stricter requirements.


## Version 0.1.9 [2009-09-22]

### Documentation

 * Now the package description lists alternative packages.

### Bug Fixes

 * From R v2.10.0, `writeValues()` of `AbstractFileArray` would give
   "Error: 4 arguments passed to `.Internal(writeBin)` which requires
   5". Updated so it works with all versions of R.


## Version 0.1.8 [2009-06-11]

### Miscellaneous

 * Made it explicit in the title and the description that this package
   should now be considered deprecated.


## Version 0.1.7 [2009-05-20]

### New Features

 * Now `open()` of `AbstractFileArray` first tries to open the file
   for reading and updating (as before).  If that fails, then it tries
   to open the file for reading only.  It might be that the file is
   only used for reading, so if the permission allows for that but not
   updating, then open it.

 * EXCEPTION HANDLING: Methods that creates/modifies files will give a
   clear error message if the file permissions does not allow it.


## Version 0.1.6 [2008-07-03]

### Significant Changes

 * Renamed the HISTORY file to NEWS.

### Miscellaneous

 * Moved internal `readBinFragments()` and `writeBinFragments()` to
   **R.utils**.

 * No bug fixes was made in this version.


## Version 0.1.5 [2006-08-29]

### New Features

 * Now the startup message when loading the package is generated with
   `packageStartupMessage()` so that it can be suppressed.

### Bug Fixes

 * Argument `dimOrder` of the `AbstractFileArray` constructor was not
   recognized causing weird results if it was intended to be in a
   non-increasing order, e.g. `FileMatrix(..., byrow=TRUE)`.

 * Reading/writing data from and to a `FileMatrix` via `[()` / `[<-()`
   was broken. Thanks Jens Oehlschlägel for troubleshooting and
   reporting this.

### Miscellaneous

 * Added private `readBinFragments()` and `writeBinFragments()`.

 * Added tests/ scripts.


## Version 0.1.4 [2006-05-21]

### Miscellaneous

 * Committed to CRAN.

 * Package passed `R CMD check` on R v2.5.0 and R v2.6.0 devel.


## Version 0.1.3 [2006-05-09]

### Miscellaneous

 * Package passed `R CMD check` on R v2.5.0.

 * Added more Rdoc comments.


## Version 0.1.2 [2006-03-14]

### New Features

 * Added `getComments()` and `setComments()` to `AbstractFileArray`.

 * Added a default buffer of free bytes after the header
   comments. This will make it easier to update the comments.  Had to
   change the file format.


## Version 0.1.1 [2006-01-28]

### New Features

 * Added `FileVector` and abstract superclass `AbstractFileArray`. The
   `FileVector` class is now used by the APS methods in the
   **affxparser.extras** package.


## Version 0.1.0 [2006-01-22]

### New Features

 * Created.  The main purpose is to provide quick and easy access to
   large number of microarray data sets.  All code is currently
   written in plain R, but will most likely be re-implemented bit by
   bit in native code to speed up the access further.  When this will
   happen I do not know.


