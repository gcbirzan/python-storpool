Description
===========

This package contains Python bindings to the JSON-over-HTTP API of the StorPool
distributed storage software.

For more information about the available API functions please see
the apidoc.html file.

StorPool is distributed data storage software running on standard x86 servers.
StorPool aggregates the performance and capacity of all drives into a shared
pool of storage distributed among the servers.  Within this storage pool the
user creates thin-provisioned volumes that are exposed to the clients as block
devices.  StorPool consists of two parts wrapped in one package - a server and
a client.  The StorPool server allows a hypervisor to act as a storage node,
while the StorPool client allows a hypervisor node to access the storage pool
and act as a compute node.

Version history
===============

1.1.0
-----

- add the get() method with a default value to SPConfig objects

1.0.5
-----

- add the SnapshotUpdateDesc type, since snapshotUpdate() only accepts a subset
  of volumeUpdate()'s parameters
- add the volumeTemplateStatus(), diskIgnore(), volumeAbandonDisk() and
  snapshotAbandonDisk() commands
- add the "bind" parameter to volumeUpdate() and snapshotUpdate()
- add the "baseOn" parameter to volumeCreate()
- add some internal templateId attributes; they are returned by the StorPool
  management service, but they should not really be used by consumers
- fix the validation of snapshot names to accept the anonymous snapshots that
  may be returned by the various "list snapshots" commands
- properly return information about missing/down disks in disksList() and
  serverDisksList() - introduce a separate type for them
- make the objects returned by the API calls iterable - "for i in obj" is now
  similar to a dictionary's iteritems() method
- make volumeCreate()'s "size" parameter optional, since the size may be
  defined in a volume template

1.0.4
-----

- rename Disk.ok to Disk.up
- fix typo: CientID => ClientID
- clean-up/fix peer ID types
- mark a bunch of attributes as internal
- use js.dumps and not str when printing values in the documentation
- generate better json for optional and internal values in the documentation
- export changes to ClusterStatus due to AoE and mgmt failover
- add AoE commands
- add the optional "propagate" parameter to volumeTemplateUpdate()
- extend the validation regular expressions for the names of volumes and
  snapshots to support the special notation for system volumes and
  snapshots currently being deleted
- fix the ActiveRequestDesc "name" parameter to also support snapshot names
- add the "snapshot" flag to the volumeStatus() result to signify that this
  entry represents a snapshot and not a volume

1.0.3
-----

- update the API documentation
- fix a HTTPConnection usage bug

1.0.2
-----

- fix the author e-mail address in setup.py
- fix the README file's Markdown format

1.0.1
-----

- relicense under the Apache 2.0 License
- switch the README file to Markdown format
- remove a leftover OpenStack reference from the README file

1.0.0
-----

- first public release
