# EasyAddon 1.21.11 Testing Checklist

## Build verification

Run:

```bash
./gradlew clean build --stacktrace --console=plain
```

Expected result:

- [ ] Build finishes with `BUILD SUCCESSFUL`.
- [ ] `build/libs/easy-addon-0.0.8.jar` is generated.
- [ ] No `NoSuchMethodError`, `NoSuchFieldError`, or remap errors during build.

## Runtime verification

Run:

```bash
./gradlew runClient --stacktrace --console=plain
```

Expected result:

- [ ] Minecraft `1.21.11` reaches the title screen.
- [ ] Fabric Loader starts successfully.
- [ ] Meteor Client `1.21.11` loads.
- [ ] Baritone / `baritone-meteor` loads.
- [ ] EasyAddon loads.
- [ ] Meteor GUI opens.
- [ ] EasyAddon category appears.
- [ ] All 7 modules appear:
  - [ ] AutoLoginXin
  - [ ] BaseFinderXin
  - [ ] ChickenNametags
  - [ ] ElytraFlyXin
  - [ ] ElytraReplace
  - [ ] NetherElytraPath
  - [ ] SimpleElytraFlyPath

## Module smoke tests

Toggle each module once while in a world:

- [ ] AutoLoginXin toggles without crash.
- [ ] BaseFinderXin toggles without crash.
- [ ] ChickenNametags toggles without crash.
- [ ] ElytraFlyXin toggles without crash.
- [ ] ElytraReplace toggles without crash.
- [ ] NetherElytraPath toggles without crash when Baritone is installed.
- [ ] SimpleElytraFlyPath toggles without crash.

## Log checks

Check `.minecraft/logs/latest.log` or `run/logs/latest.log` for:

- [ ] No `MixinApplyError`.
- [ ] No `InvalidInjectionException`.
- [ ] No `NoClassDefFoundError`.
- [ ] No `NoSuchMethodError`.
- [ ] No `NoSuchFieldError`.
- [ ] No `NullPointerException` from `me.idhammai.addon`.
- [ ] No `ClassCastException` from `me.idhammai.addon`.

## Current local verification status

This prepared ZIP could not be built or launched inside the current container because the container has no network access for downloading Gradle and Maven dependencies. The code changes are an initial compatibility pass and still need the checklist above on a normal development machine.
