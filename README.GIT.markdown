Using vcsrepo with Git
======================

To create a blank repository
----------------------------

Define a `vcsrepo` without a `source` or `revision`:

    vcsrepo { "/path/to/repo":
      ensure => present,
      provider => git
    }

If you're defining this for a central/"official" repository, you'll
probably want to make it a "bare" repository.  Do this by setting
`ensure` to `bare` instead of `present`:

    vcsrepo { "/path/to/repo":
        ensure => bare,
        provider => git
    }

To clone/pull a repository
----------------------------

To get the current [master] HEAD:

    vcsrepo { "/path/to/repo":
        ensure => present,
        provider => git,
        source => "git://example.com/repo.git"
    }

For a specific revision or branch (can be a commit SHA, tag or branch name):

    vcsrepo { "/path/to/repo":
        ensure => present,
        provider => git,
        source => 'git://example.com/repo.git',
        revision => '0c466b8a5a45f6cd7de82c08df2fb4ce1e920a31'
    }

    vcsrepo { "/path/to/repo":
        ensure => present,
        provider => git,
        source => 'git://example.com/repo.git',
        revision => '1.1.2rc1'
    }

    vcsrepo { "/path/to/repo":
        ensure => present,
        provider => git,
        source => 'git://example.com/repo.git',
        revision => 'development'
    }

For sources that use SSH (eg, `username@server:...`)
----------------------------------------------------

Manage your SSH keys with Puppet and use `require` in your `vcsrepo`
to ensure they are present.  For more information, see the `require`
metaparameter documentation[1].

More Examples
-------------

For examples you can run, see `examples/git/`

[1]: http://docs.puppetlabs.com/references/stable/metaparameter.html#require

