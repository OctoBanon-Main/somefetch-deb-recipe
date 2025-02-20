# Somefetch Debian package build recipe

**"Recipe" for building deb package for somefetch**

## Prerequisites

Before building the project, ensure you have the following installed:

`build-essential`

`devscripts`

`debhelper`

`dh-make`

`dh-cargo`

You can install them using:

```bash
sudo apt update && sudo apt install -y build-essential devscripts debhelper dh-make dh-cargo
```

## Steps to Build

1. Clone repository:
```bash
git clone https://github.com/OctoBanon-Main/somefetch-debian.git
cd somefetch-debian
```

2. Ensure the `debian/` directory is present and properly configured.

3. Fetch the upstream source:
```bash
uscan --download-current-version
tar xf ../somefetch_*.orig.tar.gz --strip-components=1
````

4. Build the package using dpkg-buildpackage:
```bash
dpkg-buildpackage -us -uc
```
or with GPG sign
```bash
dpkg-buildpackage -k"youremail@example.com (or GPG key ID)"
```

5. After a successful build, the .deb package will be available in the parent directory.

## Testing package
To install and test the build package, run:
```bash
sudo apt install ./somefetch_*.deb
```
or
```bash
sudo dpkg -i ./somefetch_*.deb
```
And run the program with the command:
```bash
somefetch
```

## See also

- [somefetch](https://github.com/UnixAwesomes/somefetch) - Minimalistic fetch for unix-like systems by UnixAwesomes
