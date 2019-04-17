# suse_mirror

SuSE package repository mirroring tool

SuSE provides their own mirroring tool however, it relies on being run from a
SuSE/SLES system.  There are cases where a site must support multiple
operating systems and thus the mirror may not be housed on a SuSE/SLES system.
This script is a relatively simple python script that can mirror the SuSE
packages repositories from any system.

Note:
This script does require an active SuSE subscription (https://www.suse.com/support/)


## Dependencies

### Debian

    python3
    python3-bs4
    python-configparser
    python-requests
    python3-requests
    python3-urllib3

### CentOS/RedHat

    python-configparser
    python-beautifulsoup4
    python-requests
    python-urllib3


## Installation

For now, installation is a manual process.

    * Create configuration directory
        mkdir /etc/suse_mirror
        chown root.root /etc/suse_mirror
        chmod 0750 /etc/suse_mirror

    * Create configuration files
        * suse_mirror.conf
            cp etc/suse_mirror.conf.example /etc/suse_mirror/suse_mirror.conf
            chown root.root /etc/suse_mirror/suse_mirror.conf
            chmod 0640 /etc/suse_mirror/suse_mirror.conf
            # Edit /etc/suse_mirror/suse_mirror.conf accordingly
        * exclude.repos
            cp etc/exclude.repos.example /etc/suse_mirror/exclude.repos
            chown root.root /etc/suse_mirror/exclude.repos
            chmod 0640 /etc/suse_mirror/exclude.repos
            # Edit /etc/suse_mirror/exclude.repos accordingly

    * Copy suse_mirror
        cp suse_mirror /usr/sbin
        chown root.root /usr/sbin/suse_mirror
        chmod 0750 /usr/sbin/suse_mirror


## Usage

    usage: suse_mirror [-h] [-C CONFIG_FILE] [-d] [-m MAX_RETRIES] [-s]
                       [-t NTHREADS] [-v] [-V] [--list-available-repos]
                       [--list-available-distros]
                       [--list-distro-repos DISTRO_TARGET]

    SuSE package repository mirroing tool

    optional arguments:
      -h, --help            show this help message and exit
      -C CONFIG_FILE, --config CONFIG_FILE
                            Specify an alternate configuration file [default:
                            /etc/suse-mirror.conf]
      -d, --debug           Print extra debugging messages
      -m MAX_RETRIES, --max-retries MAX_RETRIES
                            Specify the maximum number of times to try retrieving
                            metadata and files
      -s, --syslog          Log messages to syslog
      -t NTHREADS, --threads NTHREADS
                            Specify the number of threads to use [default: None]
      -v, --verbose         Print more verbose output (may be specified more than
                            once)
      -V, --version         Print version information

    Query options:
      --list-available-repos
                            List the repositories available to this subscription
      --list-available-distros
                            List the distro targets available to this subscription
      --list-distro-repos DISTRO_TARGET
                            List repositories for a specific distro target
                            available to this subscription

