# linux-trainers
Linux Native Trainers

A collection of binary-only Linux native game trainers.

I started making these because the native Linux trainer scene is extremely limited. Most existing solutions rely on Windows trainers through Wine/Proton, Cheat Engine setups, or fragile launch scripts that constantly break whenever Proton, Steam, or the game updates.

After getting tired of maintaining workaround scripts that were often abandoned or broken after updates, I decided to create native trainers that work directly on Linux without extra layers, compatibility hacks, or complicated setup.

Goals
- Native Linux support
- Simple usage
- No Wine or Cheat Engine required
- Minimal dependencies
- Stable standalone binaries
- No constantly breaking launcher scripts

Notes

These releases are provided as binary-only executables.
The focus of this project is ease of use and long-term maintainability for Linux users.

## Disclaimer

These trainers are provided **as-is**, with no warranty of any kind.

They work by reading and modifying the target game's memory at runtime. That is inherently risky: a wrong address, a sig that drifts after a game patch, a cheat enabled at the wrong moment, or a value the game later writes back to disk can corrupt save files, character state, or the game install itself.

Use at your own risk. Always back up your saves before enabling cheats. **I take no responsibility for any damage, data loss, lost progress, account action, or any other consequence of running these trainers.**

## Available trainers

| Game | Game Version | Trainer | Download |
|------|--------------|---------|----------|
| Cyberpunk 2077 | 2.31 | 0.17.0 | [AppImage](https://github.com/styxke/linux-trainers/releases/download/game/cyberpunk_2077/Trainer-cyberpunk_2077-2.31-0.17.0-x86_64.AppImage) · [signature](https://github.com/styxke/linux-trainers/releases/download/game/cyberpunk_2077/Trainer-cyberpunk_2077-2.31-0.17.0-x86_64.AppImage.asc) |
| Dead Space | latest | 0.6.0 | [AppImage](https://github.com/styxke/linux-trainers/releases/download/game/deadspace/Trainer-deadspace-latest-0.6.0-x86_64.AppImage) · [signature](https://github.com/styxke/linux-trainers/releases/download/game/deadspace/Trainer-deadspace-latest-0.6.0-x86_64.AppImage.asc) |
| Octopath Traveler 2 | latest | 0.3.0 | [AppImage](https://github.com/styxke/linux-trainers/releases/download/game/ot2/Trainer-ot2-latest-0.3.0-x86_64.AppImage) · [signature](https://github.com/styxke/linux-trainers/releases/download/game/ot2/Trainer-ot2-latest-0.3.0-x86_64.AppImage.asc) |

## Verifying release authenticity

All AppImages are signed with the trainer's release key. Verify before running.

**Public key fingerprint:**

```
BFA3 4675 5C58 2330 5050  A68C 6F49 E5C6 D7C3 14C8
```

**Import the public key** (one time):

```bash
# Option A — from this repo
curl -L https://raw.githubusercontent.com/styxke/linux-trainers/main/keys/trainer-pubkey.asc | gpg --import

# Option B — from a keyserver
gpg --keyserver keys.openpgp.org --recv-keys BFA346755C5823305050A68C6F49E5C6D7C314C8
```

**Verify a downloaded AppImage** (example — use the file you actually downloaded):

```bash
gpg --verify Trainer-ot2-latest-0.3.0-x86_64.AppImage.asc \
            Trainer-ot2-latest-0.3.0-x86_64.AppImage
```

Expected output:

```
gpg: Good signature from "styx <styx@users.noreply.github.com>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: BFA3 4675 5C58 2330 5050  A68C 6F49 E5C6 D7C3 14C8
```

The fingerprint at the bottom MUST match the one above. The "not certified" warning is normal unless you've explicitly trust-signed the key (`gpg --lsign-key`); it doesn't mean the signature is bad.

**If verification fails** (`BAD signature` or no `.asc` file):
- The file may be tampered with
- You may have downloaded from a fake mirror
- Don't run it

## What signing does and doesn't guarantee

- ✅ Confirms the AppImage was produced by whoever holds the private key matching the fingerprint above
- ✅ Confirms the AppImage hasn't been modified after signing
- ❌ Doesn't make the AppImage safer to run — only proves origin + integrity
- ❌ Doesn't protect you if you trust a malicious key (always verify the fingerprint above against multiple sources before importing)
