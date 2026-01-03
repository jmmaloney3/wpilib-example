# Gradle Wrapper Files

This directory contains the Gradle Wrapper files (`gradle-wrapper.jar` and `gradle-wrapper.properties`), which are **intentionally committed to version control**.

## What is the Gradle Wrapper?

The Gradle Wrapper is a small bootstrap executable that ensures everyone on the team uses the same Gradle version. It automatically downloads and uses the Gradle distribution specified in `gradle-wrapper.properties` (currently Gradle 8.11).

## Why Are These Files Committed to Git?

These files are committed to ensure:

1. **Consistency**: All team members use the exact same Gradle wrapper version, eliminating potential build inconsistencies
2. **Reproducibility**: Builds are reproducible across different machines and environments
3. **Offline Support**: Once downloaded, builds can work offline (the wrapper downloads Gradle on first use)
4. **Zero Setup**: New team members can build immediately without installing Gradle manually
5. **Standard Practice**: This follows [Gradle's official recommendations](https://docs.gradle.org/current/userguide/gradle_wrapper.html)

## What If I Need to Update Gradle?

If you need to update the Gradle version, update the `distributionUrl` in `gradle-wrapper.properties` and regenerate the wrapper using:

```bash
./gradlew wrapper --gradle-version <new-version>
```

Then commit both the updated `gradle-wrapper.properties` and the new `gradle-wrapper.jar`.

## Files in This Directory

- `gradle-wrapper.jar`: The wrapper executable (~60KB)
- `gradle-wrapper.properties`: Configuration specifying which Gradle version to use

**Do not delete or ignore these files** - they are essential for the project to build correctly.

