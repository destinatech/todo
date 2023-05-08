# / INFRA / CLUSTERS

List of active and planned compute clusters currently in service.

**NOTE!** For security reasons, do *not* publish Internet-accessible names and
addresses anywhere in this repository.  Such data must only be published via
the internal wiki <https://wiki.core.destinatech>.

## Cluster Types

We presently have two different types of cluster deployed.

The first, known as `core`, provides all internal-only support services such as
the aforementioned internal wiki, various other HTTP/S services, Intranet file,
print and e-mail services, and so on.

The second is the `svc` type cluster which provides all the Internet-facing
services, such as the *Destinatech Hello* service, web servers, etc.

We currently have a single `svc` type cluster, which is being built from the
ground up and will provide for the main development testbed where all products,
past, present and future, will be hosted.

A further two `svc` type clusters for testing and production are planned for
when the developent cluster as a whole, in terms of software functionality
and stability, etc., are nearer alpha quality.

## Active Clusters

### core

The `core` cluster consists of two enterprise-class 4U servers equipped with
3rd generation *Intel Xeon Scalable* proccessors with 8 cores and 16GB RAM
each as well as over a dozen `Raspberry Pi 4` (8GB version) Model Bs.

### svc

The development `svc` cluster consists of 4 *Ampere A1 Compute instances*
hosted at *Oracle Cloud* each with two vCPUs and 12GB RAM.

*Note: due to the software involved and limitations/quirks thereof, `svc`
clusters have a minimum node count of  three.*

<!--
vim: ts=2 sw=2 et fdm=marker :
-->
