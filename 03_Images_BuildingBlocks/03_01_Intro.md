# This section 
- All about images, the building blocks of containers
- What's in an image (and what isn't)
- Using Docker Hub registry
- Managing our local image cache
- Building our own images

## Whats an Image (and what isn't)
- App binaries and dependencies
- Metadata about the image data and how to run the image
- Official definition : <br>
    " An image is an ordered collection of root filesystem changes and the corresponding execution parameters for use within a container runtime."
- Not a complete OS. No kernel, kernel modules (eg. drivers)
- Small as one file (your app binary) like a golang static binary
- Big as a Ubuntu distro