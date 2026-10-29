# Darek Maps — data mirror

OpenStreetMap extracts, mirrored byte-for-byte from
[Geofabrik](https://download.geofabrik.de/) so that a deployment which cannot
reach Geofabrik directly can still fetch the file Geofabrik published.

Nothing here is produced by this project. Each release says which Geofabrik
file it mirrors and carries that file's **published MD5**, so a consumer
verifies against Geofabrik's own checksum rather than against anything this
repository asserts. The checksum is also pinned in the consumer's
configuration, in version control, which is a stronger check than fetching it
from the same host that serves the file.

## Attribution

© OpenStreetMap contributors.

The data is made available under the
[Open Database License (ODbL) v1.0](https://opendatacommons.org/licenses/odbl/1-0/).
Any use must keep this attribution and the same licence. See
[openstreetmap.org/copyright](https://www.openstreetmap.org/copyright).

## Why this exists

Large mirrors of free data refuse connections from datacentre address ranges
they have had trouble with, and which address a hosting platform hands you is
not something a deployment controls. When that happens the extract cannot be
downloaded on the server at all. Mirroring the file — downloaded from
Geofabrik and verified against Geofabrik's MD5 before it goes anywhere — keeps
the provenance exact and makes the mirror pure transport.

The code that consumes this lives elsewhere; this repository holds data only.
