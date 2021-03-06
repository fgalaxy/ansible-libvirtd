.. _libvirtd__ref_changelog:

Changelog
=========

.. include:: includes/all.rst

**debops.libvirtd**

This project adheres to `Semantic Versioning <http://semver.org/spec/v2.0.0.html>`__
and `human-readable changelog <http://keepachangelog.com/en/0.3.0/>`__.

The current role maintainer_ is drybjed_.


`debops.libvirtd master`_ - unreleased
--------------------------------------

.. _debops.libvirtd master: https://github.com/debops/ansible-libvirtd/compare/v0.2.0...master

Added
~~~~~

- Add ``qemu-utils`` package to list of installed packages. [bfabio_]

- Add optional support for `Kernel same-page merging <https://en.wikipedia.org/wiki/Kernel_same-page_merging>`_.
  It's not enabled by default due to potential security risks. [gaudenz]

Changed
~~~~~~~

- Change how the role detects the :command:`libvirtd` UNIX access group. [fyhertz]

- Update documentation and Changelog. [ypid_, drybjed_]

- Rename the ``libvirtd__group_map`` variable to
  :envvar:`libvirtd__access_groups`. [drybjed_]

- Use the ``getent`` Ansible module to get the list of UNIX groups present on
  the host. [drybjed_]


`debops.libvirtd v0.2.0`_ - 2016-05-19
--------------------------------------

.. _debops.libvirtd v0.2.0: https://github.com/debops/ansible-libvirtd/compare/v0.1.2...v0.2.0

Changed
~~~~~~~

- Fix deprecation warnings in Ansible 2.1.0. [ypid_]

- Fix issue with wrong variable type conversion. [drybjed_]

- Changed variable namespace from ``libvirtd_`` to ``libvirtd__``.
  ``libvirtd_[^_]`` variables are hereby deprecated.

  You might need to update your inventory. This oneliner might come in handy to
  do this:

  .. code:: shell

     git ls-files -z | xargs --null -I '{}' find '{}' -type f -print0 \
     | xargs --null sed --in-place --regexp-extended 's/\<(libvirtd)_([^_])/\1__\2/g;'

  [ypid_]

Removed
~~~~~~~

- Remove most of the Ansible role dependencies, leaving only those that are
  required for the role to run correctly.

  Configuration of dependent services like firewall, TCP Wrappers, APT
  preferences is set in separate default variables. These variables can be used
  by Ansible playbooks to configure settings related to :program:`libvirtd` in other
  services. [ypid_]


`debops.libvirtd v0.1.2`_ - 2015-11-12
--------------------------------------

.. _debops.libvirtd v0.1.2: https://github.com/debops/ansible-libvirtd/compare/v0.1.1...v0.1.2

Changed
~~~~~~~

- Fix issue with empty ``ansible_ssh_user`` variable on Ansible v2. [drybjed_]


`debops.libvirtd v0.1.1`_ - 2015-07-27
--------------------------------------

.. _debops.libvirtd v0.1.1: https://github.com/debops/ansible-libvirtd/compare/v0.1.0...v0.1.1

Changed
~~~~~~~

- Fix documentation formatting. [drybjed_]


debops.libvirtd v0.1.0 - 2015-07-27
-----------------------------------

Added
~~~~~

- Initial release. [drybjed_]
