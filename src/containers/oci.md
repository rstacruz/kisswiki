
can be run by runC or rkt

> December 8, 2015
> This means, for example, a user can build a container using docker build, and then run it in rkt, Amazon EC2 Container Service (ECS), Kubernetes, or Mesos, all without needing to repackage.
> OCI and appc Intersections
> - Container Image - no
> - Image distribution (and discovery?) - no
> - Runtime - yes
> - On-disk Image Format - yes
> Image distribution and discovery is another area of container standards we believe is very important. By creating a vendor-neutral, federated protocol for how containers are namespaced, discovered, and downloaded, we can provide a simple federated view for end-users while eliminating vendor lock-in and encouraging a variety of implementations. We think tools like git do a great job of this. GitHub is a very popular centralized repository, which makes it highly convenient for users to share projects, but the git protocol itself does not favor GitHub in any way. This model opens the playing field for competition, benefiting the user.
> https://coreos.com/blog/making-sense-of-standards/

<br>

> We are excited to introduce Docker Engine 1.11, our first release built on runC ™ and containerd ™. With this release, Docker is the first to ship a runtime based on OCI technology
> With this release, Docker Engine is now built on containerd, so everyone who is using Docker is now using OCI.
> https://blog.docker.com/2016/04/docker-engine-1-11-runc/

<br>

> an open, standard container image format
> The reluctance from OCI can be attributed to the fact that the body was formed recently and they wanted to keep a very narrow focus on their goal.  But major players like VMWare, Google and Red Hat backed rkt by CoreOS, sending out a very a strong message. These heavyweight are also members of OCI, so their support for rkt and appc carried a lot of weight.
> This project is tasked with creating a software shipping container image format spec (OCI Image Format) with security and naming as components.
> http://www.cio.com/article/3057579/open-source-tools/open-container-initiative-addresses-docker-coreos-image-problem.html

<br>

> an industry-backed project under the OCI with a strong technical community of industry maintainers to standardize how container images are built, verified, signed, and named.
> package once, run anywhere
> users can expect increased innovation and interoperability between container registries, build tools, and runtimes
> an open specification for a container image, the build artifact that contains everything needed to run a piece of software.
> As the Docker image format has evolved to include many features from the appc spec in the last 16 months, the OCI project is starting with the Docker v2.2 image format as its base.
> OCI Image Specification features:
> - Federated namespace
> - Content-addressable
> - Signable
> - Delegatable DNS namespace
> https://coreos.com/blog/oci-image-specification.html

<br>

> Under the new format, containers will have up to four layers:
> - a base layer that's the actual image format itself
> - another layer for "integrity and content-addressing" (presumably to address some of CoreOS's concerns about security)
> - optional layers to support image signing and federated naming based on DNS.
> decouple the image format from the runtime
> http://www.infoworld.com/article/3055992/open-source-tools/docker-and-coreos-no-longer-have-an-image-problem.html

<br>

> The OCI Image Format project creates and maintains the software shipping container image format spec (OCI Image Format). The goal of this specification is to enable the creation of interoperable tools for building, transporting, and preparing a container image to run.
> This specification defines how to create an OCI Image, which will generally be done by a build system, and output an image manifest, a filesystem serialization, and an image configuration. At a high level the image manifest contains metadata about the contents and dependencies of the image including the content-addressable identity of one or more filesystem serialization archives that will be unpacked to make up the final runnable filesystem. The image configuration includes information such as application arguments, environments, etc. The combination of the image manifest, image configuration, and one or more filesystem serializations is called the "OCI Image".
> This document outlines the OCI Image file format specifications, including the critical filesystem serialization and image manifest described above.
> The high level components of the spec include:
> - An image manifest and filesystem serialization (base layer)
> - A process of hashing the image format for integrity and content-addressing (base layer)
> - Signatures that are based on signing image content address (optional layer)
> - Naming that is federated based on DNS and can be delegated (optional layer)
> The OCI Image Format partner project is the OCI Runtime Spec project. The Runtime Specification outlines how to run a "filesystem bundle" that is unpacked on disk. At a high-level an OCI implementation would download an OCI Image then unpack that image into an OCI Runtime filesystem bundle. At this point the OCI Runtime Bundle would be run by an OCI Runtime.
>
> Q: Why doesn't this project mention distribution?
> A: Distribution, for example using HTTP as both Docker v2.2 and AppC do today, is currently out of scope on the OCI Scope Table. There has been some discussion on the TOB mailing list to make distribution an optional layer but this topic is a work in progress.
>
> Q: What happens to AppC or Docker Image Formats?
> A: Existing formats can continue to be a proving ground for technologies, as needed. The OCI Image Format project strives to provide a dependable open specification that can be shared between different tools and be evolved for years or decades of compatibility; as the deb and rpm format have.
> https://github.com/opencontainers/image-spec

<br>

> The organization has launched a project to establish a container image format specification.
> As a follow-up to the container runtime standard OCI is working on
> “I like web browser analogies. It’s like Firefox and Chrome,” he said. “Those are like Docker and rkt; it’s like both of them sharing HTML5. It’s the thing developers develop against, and the web should just work the same in the browser.
> The project’s goal is to allow developers to package and sign application containers, then run them in a variety of container engines using the build tools and execution scheme that best meets their needs.
> http://thenewstack.io/open-container-initiative-launches-container-image-format-spec/

<br>

> "Creating and maintaining formal specifications ("OCI Specifications") for container image formats and runtime, which will allow a compliant container to be portable across all major, compliant operating systems and platforms without artificial technical barriers." – OCI Charter
> https://www.opencontainers.org/charter/

<br>

> A container is simply a file system in a folder that gets booted and works on any underlying Linux filesystem so I am not sure about how conceptually a 'container format' fits there? That's one of the great things about containers. You do not need to think about storage. Simply zip the container folder and move across servers. Containers are completely portable across any Linux system today. But if you are going to use aufs or overlayfs layers to build single apps containers with constrained container OS templates then perhaps there is a need for a format.
> https://news.ycombinator.com/item?id=9762049
