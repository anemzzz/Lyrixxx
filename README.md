# Lyrix

Lyrix detects whatever song is playing on your Android device and shows the
matching synced lyrics in real time. The detection feature relies on a native
notification listener, so it only works inside a custom build of the app — not
inside Expo Go.

## Install the Android app

The easiest way to get Lyrix on your phone is to download the pre-built `.apk`
from the GitHub Releases page:

➡️ **[Download the latest Lyrix .apk](../../releases/latest)**

On the latest release, expand **Assets** and grab the file named
`lyrix-<version>-<tag>.apk`. Copy it to your Android phone, tap the file, and
allow installation from your file manager when prompted.

After installing, open Lyrix → **Detect** tab → **Open settings** → enable
**“Lyrix Lyrics Detector”** under Notification access. Come back, hit **Start
detection**, then play a song in any music app.

> Releases are produced automatically by GitHub Actions
> (`.github/workflows/android-build.yml`) every time a `v*` tag is pushed — no
> local Android toolchain required. Pushing the tag (e.g.
> `git tag v1.2.3 && git push --tags`) creates a **draft** GitHub release for
> that tag with auto-generated release notes from the commit log, then builds
> the signed `.apk` and attaches it to that same draft. Review the draft on
> the Releases page and hit **Publish** when you're ready to ship.
>
> Tagged release builds are signed with a single, persistent release keystore
> stored in the repo's GitHub Actions secrets so users can install new
> versions on top of old ones without losing their saved Library. Setting
> that keystore up is a one-time step for the maintainer — see
> ["One-time release keystore setup"](artifacts/lyrix/BUILD_ANDROID.md#one-time-release-keystore-setup-maintainers-only)
> in `BUILD_ANDROID.md`. Until it's configured, tagged builds will fail fast
> instead of producing an unupgradable `.apk`.

## Build it yourself

If you'd rather build the `.apk` from source (locally with Android Studio or
via Expo's cloud builder), follow
[`artifacts/lyrix/BUILD_ANDROID.md`](artifacts/lyrix/BUILD_ANDROID.md).

## Repo layout

This is a pnpm monorepo. The Android app lives in `artifacts/lyrix/` and the
LRCLIB API proxy lives in `artifacts/api-server/`.

