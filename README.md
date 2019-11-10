# Autoloader for WordPress classes

> Short description as in composer.json

`composer install patch/wp-autoloader`

Note: *Our package uses the same major and minor version as your software does.*


## Why? 5% less costs!

Looking at a wp-cli call for a bare naked WordPress 5.4.2
on our testing machine:

What?                       | Before    | After     | Diff
-------------------         | -------   | -----     | ----
Memory peak usage (real)    | 35651584  | 33554432  | -2.00 MB
Memory peak usage           | 34457144  | 32903120  | -1.48 MB
Memory usage (real)         | 35651584  | 33554432  | -2.00 MB
Memory usage                | 34293328  | 32739304  | -1.48 MB

So it spares around 5% of memory
and possibly some time too.
