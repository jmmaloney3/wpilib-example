# VS Code Configuration Files

This directory contains VS Code workspace configuration files that are **intentionally committed to version control**.

## Files in This Directory

### `launch.json`
Defines debug configurations for the WPILib robot project:
- **WPILib Desktop Debug**: Debug robot code running in simulation on your desktop
- **WPILib roboRIO Debug**: Debug robot code running on the physical RoboRIO hardware

These configurations are essential for debugging your robot code and are project-specific, not user-specific.

### `settings.json`
Contains workspace-specific settings that configure:
- **Java Build Configuration**: Automatic Gradle build configuration updates
- **Test Configuration**: JUnit test settings with proper library paths for native libraries (JNI)
  - Configures `LD_LIBRARY_PATH` and `DYLD_LIBRARY_PATH` to point to `build/jni/release`
  - Sets working directory for tests
  - Essential for running unit tests with WPILib native libraries
- **File Exclusions**: Hides build artifacts, IDE files, and other generated files from the VS Code file explorer
- **Code Completion**: Team-standard autocomplete preferences for common testing and WPILib APIs

## Why Are These Files Committed to Git?

These files are **project configuration**, not personal preferences, and should be version controlled because they:

1. **Enable Debugging**: Without `launch.json`, team members cannot debug the robot code in VS Code
2. **Configure Testing**: The test configuration in `settings.json` sets critical library paths that must match the project's build structure (`build/jni/release`)
3. **Ensure Consistency**: All team members get the same development environment and debugging capabilities
4. **Project-Specific Paths**: The configurations reference project-specific paths (like `${workspaceFolder}/build/jni/release`) that must be consistent across all machines
5. **Team Collaboration**: When debugging configurations are updated, all team members benefit from the changes
6. **WPILib Standard**: WPILib project templates include these files, indicating they're meant to be shared

## What About User-Specific Settings?

VS Code has two levels of settings:
- **Workspace settings** (this directory): Project-specific, should be committed
- **User settings**: Personal preferences stored in your VS Code user directory, not in the project

The files in this directory are workspace settings that configure the project itself, not your personal editor preferences. Your personal VS Code settings (font size, theme, keybindings, etc.) are stored separately and are not affected by committing these files.

## Modifying These Files

If you need to:
- **Add debug configurations**: Edit `launch.json` and commit the changes
- **Update test settings**: Edit `settings.json` and commit the changes
- **Change file exclusions**: Edit `settings.json` and commit the changes

All changes should be reviewed and committed so the entire team benefits from improvements.

**Do not ignore this directory** - these files are essential for the development workflow and should be version controlled alongside your source code.

