# PRTP

PRTP is a lightweight Paper random teleport plugin built for survival servers that need fast RTP without expensive safe-location searches.

## Target

- Paper, Spigot, or Purpur 1.21.1 through 1.21.11
- Java 21
- Gradle
- Multiverse-Core friendly through Bukkit world lookup and `softdepend`

## Behavior

- `/rtp` always teleports into the single configured world, no matter where the player starts.
- Coordinates are generated in **square radius mode** around that world's spawn.
- Chunks are loaded asynchronously on Paper/Purpur when that API is available.
- Spigot uses a compatibility fallback because Spigot does not expose Paper's async chunk API.
- PRTP checks the highest block at the generated X/Z and rejects water, lava, air, and void-like locations.
- It does not perform expensive terrain scans or infinite synchronous loops.
- If a small retry batch misses, PRTP schedules another async batch and keeps going until it finds a usable location.

## Commands

| Command | Permission | Default | Description |
| --- | --- | --- | --- |
| `/rtp` | `prtp.use` | true | Random teleport yourself |
| `/rtp <player>` | `prtp.admin` | op | Force RTP another player |
| `/rtp reload` | `prtp.admin` | op | Reload config |
| `/prtp info` | `prtp.admin` | op | Show plugin info |

## Build

```bash
gradle build
```


