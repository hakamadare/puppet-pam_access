[![Build Status](https://travis-ci.org/huit/puppet-pam_access.png?branch=master)](https://travis-ci.org/huit/puppet-pam_access)

# pam_access

This module manages **pam_access** entries stored in `/etc/security/access.conf`.  It
requires Augeas >= 0.8.0.

Sample usage:

    class { 'pam_access':
      exec => true,
    }

    pam_access::entry { 'mailman-cron':
      user   => 'mailman',
      origin => 'cron',
    }

    pam_access::entry { 'root-localonly':
      permission => '-',
      user       => 'root',
      origin     => 'ALL EXCEPT LOCAL',
    }

    pam_access::entry { 'lusers-revoke-access':
      create => false,
      user   => 'lusers',
      group  => true,
    }

Changes:

0.1.0:
    Implemented a fix for dependency cycle and more efficient insertion of access.conf elements (thanks @FutureSharks!)

0.0.2:
    Specify `incl` and `lens` parameters to augeas resources for performance improvement.

0.0.1:
    Initial release.
