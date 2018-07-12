# eslint-scope virus scan

RunKit is in the unique position where we have the built source of every package
on npm readily available, so we've kicked off an initial simple scan of every
package currently published to see if we detect the additional presence of this
virus in the registry. The process is ongoing and we will be updating this
README with our findings, as well as filing issues on any projects if we get a
positive hit. We have already found one instance that was previously unreported
that is detailed below.

This is a fairly simplestic scan, just searching for the strings
`sstatic1.histats.com` and `raw/XLeVP82h`, designed to quickly mitigate and
discover any pure copies of this virus, and probably won't catch cases where the
code has been significantly altered. We are open to suggestions from the
community about additional steps we could take. Again, we're in a position few
others are to actually check all the source, and so we feel it is our
responsibility to help in any way we can.

Ultimately, we are hoping that this was caught fast enough to not have had a
chance to spread, and that this work will be in an abondance of caution. The
node community is certainly large enough where "enough eyes [may] make every
vulnerability shallow", and the already great (and quick!) work by the
eslint-scope team and npm have hopefully stopped this before it had a chance to
grow.

## Known Packages With Vulnerability

1. ### eslint-scope@3.7.2

   | status | bug |
   |--------|---------------|
   | unpublished | [GitHub issue](https://github.com/eslint/eslint-scope/issues/39) |

   The package that we believe had the original vulnerability.
   
2. ### eslint-config-eslint@5.0.2

   | status | bug |
   |--------|---------------|
   | unpublished | [GitHub issue](https://github.com/eslint/eslint-scope/issues/39) |
  
   A related package that was quickly discovered to also contain the vulnerability.

3. ### eslint-config-airbnb-standard@2.0.0

   | status | bug |
   |--------|---------------|
   | **still vulnerable** | [GitHub issue](https://github.com/doasync/eslint-config-airbnb-standard/issues/3) |
   
   RunKit's virus scan detected that `eslint-config-airbnb-standard@2.0.0` contains `eslint-scope@3.7.2` in its `bundleDependencies`, which means that version will always be susceptible to the bug despite not being directly affected by it. Given that the virus takes action during installation and eslint-scope is present in `bundledDependencies`, it is **possible** that the bug won't have a chance to take effect. However, we have no thoroughly tested this and it is recommended you move away from this version either way.
