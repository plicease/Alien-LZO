# Alien::LZO [![Build Status](https://secure.travis-ci.org/plicease/Alien-LZO.png)](http://travis-ci.org/plicease/Alien-LZO)

Build and make available LZO

# SYNOPSIS

In your Build.PL:

    use Module::Build;
    use Alien::LZO;
    my $builder = Module::Build->new(
      ...
      configure_requires => {
        'Alien::LZO' => '0',
        ...
      },
      extra_compiler_flags => Alien::LZO->cflags,
      extra_linker_flags   => Alien::LZO->libs,
      ...
    );
    
    $build->create_build_script;

In your Makefile.PL:

    use ExtUtils::MakeMaker;
    use Config;
    use Alien::LZO;
    
    WriteMakefile(
      ...
      CONFIGURE_REQUIRES => {
        'Alien::LZO' => '0',
      },
      CCFLAGS => Alien::LZO->cflags . " $Config{ccflags}",
      LIBS    => [ Alien::LZO->libs ],
      ...
    );

In your [FFI::Platypus](https://metacpan.org/pod/FFI::Platypus) script or module:

    use FFI::Platypus;
    use Alien::LZO;
    
    my $ffi = FFI::Platypus->new(
      lib => [ Alien::LZO->dynamic_libs ],
    );

# DESCRIPTION

This distribution provides lzo so that it can be used by other 
Perl distributions that are on CPAN.  It does this by first trying to 
detect an existing install of lzo on your system.  If found it 
will use that.  If it cannot be found, the source code will be downloaded
from the internet and it will be installed in a private share location
for the use of other modules.

# SEE ALSO

[Alien](https://metacpan.org/pod/Alien), [Alien::Base](https://metacpan.org/pod/Alien::Base), [Alien::Build::Manual::AlienUser](https://metacpan.org/pod/Alien::Build::Manual::AlienUser)

# AUTHOR

Graham Ollis <plicease@cpan.org>

# COPYRIGHT AND LICENSE

This software is copyright (c) 2017 by Graham Ollis.

This is free software; you can redistribute it and/or modify it under
the same terms as the Perl 5 programming language system itself.
