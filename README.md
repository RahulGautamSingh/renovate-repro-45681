# renovate-repro-45681

Minimal reproduction for https://github.com/renovatebot/renovate/discussions/45681

An npm workspace whose workspace package pins a dependency at an exact version.
Renovate's lockstep-sibling massage (renovatebot/renovate#45085) deletes the
`packages/app` entry from `package-lock.json`, leaving `node_modules/@repro/app`
pointing at a link target that no longer exists, so the artifact update fails:

```text
npm error code EMISSINGTARGET
npm error Missing target in lock file: "packages/app" is referenced by "node_modules/@repro/app" but does not exist.
```

Fix: renovatebot/renovate#45786
