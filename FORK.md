# Cloudflare.Kit source fork

This is an independently maintained fork of Alos-no/Cloudflare.NET, not an official
upstream release. Original Apache-2.0 licensing and copyright notices are retained.

- Upstream baseline: `dd11a749db394f2b8d4517bd0ffb56f4ba1c0244` (API 3.7.0, R2 2.5.0).
- Maintenance branch: `kit` at https://github.com/bighamx/Cloudflare.NET.
- Consumer: https://github.com/bighamx/Cloudflare.Kit, pinned by Git submodule commit.

Modified files:

- `src/Cloudflare.NET/Dns/Models/DnsRecordModels.cs`: retain Worker ownership,
  nullable read-only metadata and unknown JSON properties. Existing positional
  constructors and deconstruction remain unchanged.
- `src/Cloudflare.NET/Cloudflare.NET.csproj`: fork package Cloudflare.Kit.Api 3.7.0.2,
  preserving assembly version 3.7.0.0 and the original signing key.
- `src/Cloudflare.NET.R2/Cloudflare.NET.R2.csproj`: fork package Cloudflare.Kit.R2 2.5.0.1,
  preserving assembly version 2.5.0.0 and the original signing key.
- `Directory.Build.props`: .NET 8 target, fork repository URL/readme, explicit packaging.

Fork packages use distinct IDs for publication on NuGet.org; assembly names,
namespaces and signing identities remain unchanged for binary compatibility.
Do not reference the official Cloudflare.NET.Api or Cloudflare.NET.R2 packages
alongside the fork packages, as they contain the same assembly identities.
Both API and R2 are built from source to avoid mixing official
package references with the fork project references. DNS regression tests are in
the consuming Kit repository.

To update, fetch https://github.com/Alos-no/Cloudflare.NET and merge the desired
upstream revision into `kit`. Review compatibility, update this baseline and the
fork package versions, run the Kit build/tests/package checks, then commit the new
submodule revision in Kit. Do not automatically track upstream HEAD.
