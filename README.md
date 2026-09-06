# EatMe — Android beta channel

Public download point for the **Android beta** of [EatMe](https://eatme-app.com),
and the manifest the app's own update check reads.

There is **no source code here.** EatMe is developed in a private repository;
this one exists because a GitHub Release in a private repo cannot be downloaded
without a token, and a beta tester should only ever need a link.

## Getting the app

Grab the newest `.apk` from [Releases](../../releases/latest) and open it on your
phone. Android will ask whether this browser may install apps — that permission
is what "installing from outside the Play Store" means, and you can revoke it
again afterwards.

Every APK here is signed with the same key, so each new one installs **over** the
last and your kitchen, lists and recipes stay where they are. If Android refuses
the install with "app not installed", you have a build signed by a different key
(most likely an old test build) — uninstall it first.

Builds are cut from the private repository's release workflow. Nothing is ever
uploaded here by hand.

## `android-latest.json`

The installed app checks this file to notice that a newer build exists:

```jsonc
{
  "versionCode": 534,            // Android versionCode; compared against the installed build
  "version": "1.1.1-beta",       // marketing version, for display
  "tag": "v1.1.1-beta",
  "apkUrl": "https://github.com/EatMe-App/eatme-beta/releases/download/v1.1.1-beta/EatMe-v1.1.1-beta.apk",
  "apkSizeBytes": 78123456,
  "publishedAt": "2026-09-06T14:43:17Z"
}
```

`versionCode` is the only field the decision is made on, and it is the commit
count of the release, so it only ever goes up. The app refuses any `apkUrl` that
is not a release asset of this repository.

## iOS

There is no iOS build here. iOS testing runs through TestFlight, which updates
itself.

## Afterwards

This whole channel is temporary scaffolding for the beta. Once EatMe is in the
Play Store, the store does this job and the repository can be deleted.
