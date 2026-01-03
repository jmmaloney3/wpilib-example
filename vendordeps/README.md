# Vendor Dependencies (vendordeps)

This directory contains JSON configuration files that define third-party vendor libraries used by this WPILib robot project.

## What Are Vendor Dependencies?

Vendor dependencies are third-party libraries provided by FRC hardware vendors (such as REV Robotics, CTRE Phoenix, NavX, PathPlanner, etc.) that extend WPILib's capabilities. These JSON files tell GradleRIO how to download, configure, and include these libraries in your build.

## Files in This Directory

Each `.json` file in this directory represents a vendor library dependency. For example:
- `WPILibNewCommands.json` - Defines the WPILib New Commands framework

When you add vendor libraries through WPILib's vendor dependency system, their JSON configuration files are placed here.

## Why Are These Files Committed to Git?

These files are **intentionally committed to version control** because they:

1. **Define Project Dependencies**: Like `build.gradle`, these files specify which vendor libraries your project uses and their versions
2. **Ensure Team Consistency**: All team members will use the exact same vendor libraries and versions, preventing "works on my machine" issues
3. **Enable Reproducible Builds**: New team members can clone the repository and build immediately with the correct dependencies
4. **Track Configuration Changes**: Version control allows you to see when vendor dependencies were added, removed, or updated
5. **Required for Builds**: GradleRIO reads these files during the build process (referenced via `wpi.java.vendor.java()` in `build.gradle`)

## Adding Vendor Dependencies

To add a new vendor dependency:

1. Use WPILib's vendor dependency installer (in VS Code: WPILib: Manage Vendor Libraries)
2. Or manually download the vendor dependency JSON file and place it in this directory
3. Commit the new JSON file to git so all team members have it

## Removing Vendor Dependencies

If you remove a vendor library from your project:

1. Delete the corresponding JSON file from this directory
2. Commit the deletion to git
3. All team members will automatically stop using that library after pulling

## Current Vendor Dependencies

- **WPILib-New-Commands** (`WPILibNewCommands.json`) - The WPILib New Commands framework for command-based robot programming

**Do not ignore this directory** - it is essential for the project to build correctly and should be version controlled alongside your source code.

