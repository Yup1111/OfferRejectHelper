# Cheese builds

Keep applicationId `com.local.sparkreject` unchanged for in-place updates.

The main workflow assigns version code 100000 + run number * 1000 + run attempt, and displays the version and code in the app and APK filename. Keep this workflow and its run counter; if replacing it, choose a base above all previously distributed codes. A rerun of an older run must not be distributed as the latest build.

For stable signing, configure repository Actions secret CHEESE_DEBUG_KEYSTORE_BASE64 with base64 bytes of a permanent Android debug keystore (alias androiddebugkey, standard Android debug passwords). Reuse the original signing key if available. Never commit a keystore or its base64 contents. The workflow restores it before Gradle runs. Without this secret, the runner generates an ephemeral key, and in-place installation is not guaranteed. Public certificate fingerprints are included with each APK for comparison.

A new signing key cannot update an app signed with a different key, regardless of version code. Do not uninstall the existing app casually: that removes its local settings and diagnostics.
