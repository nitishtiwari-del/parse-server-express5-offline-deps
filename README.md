# parse-server express 4 -> 5 offline dependency manifest

Manifest-only repository. It pins the **union** of the dependency graphs of
[`parse-community/parse-server`](https://github.com/parse-community/parse-server) at

* base commit `cc8dad8fa18707746c4ee87f3a2170fa9df4d5bd` (express 4.21.2, body-parser 1.20.3), and
* reference commit `e0480dfa8d97946e57eac6b74d937978f8454b3a` (express 5.0.1, router 2.0.0).

`package-lock.json` is the reference commit's lockfile plus three aliased entries for the only
`(package, version)` pairs that exist in the base lockfile and not in the reference one
(`call-bind-apply-helpers@1.0.1`, `get-intrinsic@1.2.7`, `object-inspect@1.13.3`), so a single
`npm ci` downloads every tarball both commits need.

It exists purely to warm an offline npm cache in a Docker build stage and contains no project source.
