# Building Cheese

The active project is `OfferRejectHelper-v1.0-diagnostic-source.zip`. Unpack it and open `SparkRejectHelper` in Android Studio. The other source ZIP is historical.

The main workflow runs the Java regression checks, builds the APK, verifies its signature, and uploads a named artifact. Download and extract that artifact to install its APK.

Every run uses versionCode `100000 + GITHUB_RUN_NUMBER * 1000 + GITHUB_RUN_ATTEMPT` and versionName `2.2.RUN.ATTEMPT`. Do not distribute a rerun of an older workflow run as a newer version.

The Actions secret `CHEESE_DEBUG_KEYSTORE_BASE64` is REQUIRED. Builds fail if it is absent; they never silently create another signing key. Keep the same secret and application ID (`com.local.sparkreject`) for updates in place. The ZIP must never contain a keystore or signing passwords.

Local builds default to code 22 and version 2.2-local; they are not update packages for an installed Actions build. Pass the version properties and use the same signing key when producing an update outside Actions.

## Current repair

Strict read/scroll-only mode, paced scan callbacks, clipped-header handling, bounded scan retries, detail mileage verification, and declared screenshot capability. Live Spark behavior still needs device testing. Keep automatic rejection off during this scan test.
