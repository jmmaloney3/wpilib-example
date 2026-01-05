This repository contains a simple example that can be used for experiments, prototypes and tutorials.

This repository contains:
* Simple example code
* Process documentation
* Tutorials

This line crerates a merge conflict with branch A (Change B)
Adding this to intentionally create a merge conflict!!! (Change A)

## Trunk Based Development
See `docs/trunk-based-dev-guide.md` for information about trunk based development.  This documentation describes
the team's procedures for managing code in git.

## Build Configuration Files

This project uses Gradle as its build system. The following files are essential build configuration files that **must be committed to version control**:

### `build.gradle`
The main build configuration file that defines:
- Project dependencies (WPILib, vendor libraries, JUnit)
- Build tasks (compilation, JAR creation, deployment)
- Java version compatibility (Java 17)
- RoboRIO deployment configuration
- Simulation settings

**Why version control?** This file defines the entire build process and all project dependencies. Without it, the project cannot be built.

### `settings.gradle`
Configures Gradle's project structure and plugin management:
- Defines plugin repositories (including WPILib's Maven repository)
- Configures WPILib home directory detection (cross-platform)
- Sets Gradle system properties

**Why version control?** Required for Gradle to locate plugins and dependencies. Ensures all team members use the same repository configuration.

### `gradlew` and `gradlew.bat`
Gradle wrapper scripts that allow building the project without requiring Gradle to be pre-installed:
- `gradlew` - Unix/macOS/Linux wrapper script
- `gradlew.bat` - Windows wrapper script

These scripts use the Gradle wrapper JAR (in `gradle/wrapper/`) to download and run the correct Gradle version automatically.

**Why version control?** 
- Enables zero-setup builds (no manual Gradle installation needed)
- Ensures all team members use the same Gradle version
- Cross-platform support (works on Windows, macOS, and Linux)
- Standard Gradle best practice

### Why These Files Must Be Version Controlled

All of these files are **essential project configuration** that must be version controlled because they:

1. **Define the build**: Without them, the project cannot be compiled or deployed
2. **Ensure consistency**: All team members use identical build configurations
3. **Enable reproducibility**: New team members can build immediately after cloning
4. **Track changes**: Version control shows when build configuration changes
5. **Support collaboration**: Team members can review and discuss build changes

These files work together with the `gradle/wrapper/` directory (see `gradle/wrapper/README.md`) to provide a complete, self-contained build system.

---

2026-01-03: This repository is currently a work in progress.