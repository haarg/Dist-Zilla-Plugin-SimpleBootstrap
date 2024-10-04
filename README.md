# NAME

Dist::Zilla::Plugin::SimpleBootstrap - Bootstrap a Dist::Zilla library

# SYNOPSIS

```perl
# in dist.ini
[SimpleBootstrap]

# use a plugin under lib/
[Plugin::Under::Development]
```

# DESCRIPTION

Allow using a plugin being developed in its own `dist.ini`. Unlike
[\[Bootstrap::lib\]](https://metacpan.org/pod/Dist%3A%3AZilla%3A%3APlugin%3A%3ABootstrap%3A%3Alib), it doesn't try to use
a version of the module that has been built by [Dist::Zilla](https://metacpan.org/pod/Dist%3A%3AZilla), instead always
using modules directly from `lib/`.

Additionally, it ensures that the modules are available during the build phase.
[Dist::Zilla](https://metacpan.org/pod/Dist%3A%3AZilla) localizes [`@INC`](https://metacpan.org/pod/perlvar#INC) during the initial loading
of modules, so modifications made at that time wouldn't normally persist. This
allows things like [Pod::Weaver](https://metacpan.org/pod/Pod%3A%3AWeaver) plugins to be used from the `lib/` directory.

If a `share/` directory exists, it will be set as the
[share directory](https://metacpan.org/pod/File%3A%3AShareDir#dist_dir) for the distribution.

# OPTIONS

- lib

    Can be used to specify an alternate directory to bootstrap, rather than `lib`.

- share

    Specifies the dist share directory for the distribution.

    If `module_share` is not specified, this defaults to `share`.

    Defaults to `share`.

- module\_share

    Specifies [module share directories](https://metacpan.org/pod/File%3A%3AShareDir#module_dir). Should be formatted as:

    ```
    module_share = My::Module = share
    ```

# KNOWN ISSUES

- This module will not work well when used with [Test::DZil](https://metacpan.org/pod/Test%3A%3ADZil).

# SEE ALSO

- [\[Bootstrap::lib\]](https://metacpan.org/pod/Dist%3A%3AZilla%3A%3APlugin%3A%3ABootstrap%3A%3Alib), a significantly
more complex plugin, which doesn't solve the problem of `@INC` being localized.
Also does not include handling for share directories.
- [\[lib\]](https://metacpan.org/pod/Dist%3A%3AZilla%3A%3APlugin%3A%3Alib), a simple plugin, but which doesn't
solve the problem of `@INC` being localized. Also does not include handling for
share directories.

# BUGS

Please report any bugs or feature requests on the bugtracker website
[https://github.com/haarg/Dist-Zilla-Plugin-SimpleBootstrap/issues](https://github.com/haarg/Dist-Zilla-Plugin-SimpleBootstrap/issues)

When submitting a bug or request, please include a test-file or a
patch to an existing test-file that illustrates the bug or desired
feature.

# AUTHOR

Graham Knop <haarg@haarg.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2024 by Graham Knop.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
