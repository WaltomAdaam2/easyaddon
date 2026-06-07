# EasyAddon 1.21.11 Initial Port Notes

This branch is a clean, minimal port of EasyAddon from Minecraft 1.21.1 to Minecraft 1.21.11.

## Target versions

- Minecraft: `1.21.11`
- Yarn mappings: `1.21.11+build.6`
- Fabric Loader: `0.19.3`
- Fabric Loom: `1.16.3`
- Gradle wrapper: `9.4.0`
- Java: `21`
- Meteor Client dependency: `meteordevelopment:meteor-client:1.21.11-SNAPSHOT`
- Baritone dependency: `meteordevelopment:baritone:1.21.11-SNAPSHOT`
- Baritone Fabric mod id: `baritone-meteor`

## Runtime mods required

Put these in the same Fabric 1.21.11 instance:

- Meteor Client for Minecraft `1.21.11`.
- Baritone for Minecraft `1.21.11` using the Meteor fork / mod id `baritone-meteor`.
- The built `easy-addon-0.0.8.jar` from this project.

This port does not add Litematica or MaLiLib because the source tree does not import or use those APIs.

## Build

```bash
./gradlew clean build --stacktrace --console=plain
```

The release jar should be in:

```text
build/libs/easy-addon-0.0.8.jar
```

Do not install the `-sources.jar` or `-dev.jar` file as the normal user mod.

## Development run

```bash
./gradlew runClient --stacktrace --console=plain
```

## Main compatibility changes

- Updated Minecraft, Yarn, Fabric Loader, Fabric Loom, Gradle wrapper, Meteor, and Baritone versions.
- Removed unused Litematica and MaLiLib dependencies.
- Declared Baritone as a required runtime dependency because `NetherElytraPath` directly imports Baritone APIs.
- Replaced old Elytra API usage with 1.21.11-compatible gliding checks and helper durability checks.
- Updated player yaw, selected hotbar slot, world disconnect, render, and direction APIs.
- Added null checks so modules do not immediately crash when toggled outside a world.
- Replaced the manual shulker open packet sequence with `interactionManager.interactBlock`.
- Implemented the initial firework transfer path in `NetherElytraPath.takeFireworks()` and resumes Baritone elytra pathing after transfer.

## Known limitations

This ZIP was prepared in an offline container where Gradle could not download `services.gradle.org` or Maven dependencies. Build and `runClient` still need to be executed on a machine with internet access.

`NetherElytraPath` still needs real in-game testing for the full land-place-open-transfer-resume loop because it depends on world/server timing, Baritone behavior, inventory state, and shulker placement conditions.
