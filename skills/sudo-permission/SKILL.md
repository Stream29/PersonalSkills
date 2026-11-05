---
name: sudo-permission
description: Use when an agent needs elevated privileges (sudo or run0) on local or remote devices.
---

# Sudo Permission

```kotlin
fun runSudo(command: String, device: Device = CurrentDevice) {
    when {
        device.`skill documents passwordless sudo`() -> sh("sudo $command")
        device.`skill documents weak sudo password`() ->
            `Run sudo with documented password`(command, device.password)
        `User may be away from computer`() ->
            sh("run0 $command") // Persistent GUI prompt; continues when user returns
        else -> while (true) { // Default: sudo with fingerprint auth
            try {
                sh("sudo $command")
                return
            } catch (e: FingerprintAuthTimeout) {
                sh("run0 $command")
                return
            } catch (e: FingerprintRecognitionFailed) {
                `Ask user to retry fingerprint authentication`()
            }
        }
    }
}
```

