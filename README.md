# Voxear Packages

The default registry for [Voxear](https://github.com/CookieJarTools/Voxear) packages. Voxear looks here when you add a package by its name:

```
vox package add orbit-tools
```

A package itself lives in its own Git repository. This registry only lists where each release is, so that projects can find packages by name and search them.

## How the registry is laid out

Each package has a file in `packages/`, named after the package: `packages/orbit-tools.toml`.

```toml
description = "Cameras that orbit, follow and frame"

[[version]]
version = "1.2.0"
git = "https://github.com/someone/orbit-tools"
tag = "v1.2.0"
commit = "4f0c1a7e9b2d5c8a1e3f6b9d2c5a8e1f4b7d0c3a"
engine = ">=0.1"
```

- `version`: the release's version, matching its `package.toml`.
- `git`: the repository the package is fetched from.
- `tag`: the release's tag, for people reading the file.
- `commit`: the exact commit projects fetch. A release stays the same even if its tag moves later.
- `path`: the package's folder, for a repository that holds more than one.
- `engine`: the Voxear versions the release works with.
- `yanked = true`: stops new projects picking a broken release. Projects already locked to it keep it.

## Listing your package

1. Push your package to a public Git repository, and tag a release that matches the version in its `package.toml`.
2. Fork this repository and clone your fork.
3. From your package's folder, run:

   ```
   vox package publish --registry path/to/your/clone
   ```

   This adds the release to `packages/<name>.toml`.
4. Commit that file and open a pull request.

Add each new release the same way. Package names are first come, first served. A pull request that changes another author's package will not be merged.

See the Packages pages in the Voxear manual for how to make a package.
