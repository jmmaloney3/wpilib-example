# WPILib Simulator Guide

## Overview
This guide explains how to use the WPILib simulator to test your robot code, including how to simulate joystick inputs and visualize your robot's movement on a 2D field.

## Your Robot Code
Your robot uses an `XboxController` on port 0 and reads:
- **Left Y axis** (forward/backward movement)
- **Left X axis** (turning left/right)

This is used in `teleopPeriodic()` to control the differential drive.

## Using the Simulator

### Step 1: Launch the Simulator
You've already done this! When you select "Simulate Robot Code" from the VS Code command palette, the Simulation GUI should open.

### Step 2: Enable Teleop Mode
1. In the Simulation GUI, look for the **"Robot State"** panel
2. You'll see three modes: **Disabled**, **Autonomous**, and **Teleop**
3. Click on **"Teleop"** to enable teleoperated mode (this is when your joystick code runs)

### Step 3: Add a Joystick Input
You have two options:

#### Option A: Use Keyboard (Easiest for Testing)
1. In the GUI, find the **"System Joysticks"** panel
2. You should see **"Keyboard 0"** listed
3. **Click and drag** "Keyboard 0" from "System Joysticks" to the **"Joysticks"** panel
4. This makes the keyboard available as joystick port 0 (which matches your `XboxController(0)`)

**Default Keyboard Controls** (configured in `simgui-ds.json`):
- **W/S keys**: Forward/Backward (Axis 1 - Left Y)
- **A/D keys**: Left/Right (Axis 0 - Left X)
- **Z, X, C, V**: Buttons 0-3
- **Arrow keys**: POV (D-pad)

#### Option B: Use a Physical Gamepad
1. Connect your gamepad/joystick to your computer
2. It should appear in the **"System Joysticks"** panel
3. **Click and drag** it to the **"Joysticks"** panel
4. If using an Xbox controller, you may need to enable the **"Map gamepad"** toggle in the Joysticks panel for proper mapping

### Step 4: Test Your Robot
1. Make sure **Teleop** mode is enabled (from Step 2)
2. Use your keyboard or gamepad to control the robot:
   - **W/S** keys (or left stick Y) = forward/backward
   - **A/D** keys (or left stick X) = turn left/right
3. You should see the motor outputs change in the simulation

## Understanding the GUI Panels

- **Robot State**: Shows current mode (Disabled/Autonomous/Teleop). Click to change modes.
- **System Joysticks**: Lists all joysticks/gamepads connected to your computer, plus "Keyboard 0"
- **Joysticks**: Shows joysticks that are available to your robot code (drag from System Joysticks)
- **Other Devices**: May show additional simulated hardware

## Troubleshooting

### Robot doesn't respond to inputs:
- Make sure you're in **Teleop** mode (not Disabled or Autonomous)
- Verify the joystick/keyboard is in the **"Joysticks"** panel (not just "System Joysticks")
- Check that it's on port 0 (first joystick in the list)

### Keyboard controls don't work:
- Make sure "Keyboard 0" is dragged to the "Joysticks" panel
- Try restarting the simulator
- Check `simgui-ds.json` for keyboard key mappings

### Want to customize keyboard controls:
- In the Simulation GUI menu bar, go to **DS** > **Keyboard 0 Settings**
- You can remap keys to different joystick axes and buttons

## Testing Autonomous Mode
Your robot also has autonomous code that drives forward for 2 seconds:
1. Click **"Autonomous"** in the Robot State panel
2. The robot should automatically drive forward for 2 seconds, then stop
3. No joystick input is needed for autonomous mode

## 2D Field Visualization

The WPILib simulator can display your robot's position and movement on a simulated 2D field. This allows you to see where your robot is on the field as it moves, which is especially useful for testing autonomous routines and understanding robot behavior.

### Setting Up Field2d Visualization

To enable 2D field visualization, you need to add `Field2d` to your robot code and update the robot's pose (position and rotation) in the `robotPeriodic()` method.

#### Step 1: Add Required Imports

Add these imports to your `Robot.java` file:

```java
import edu.wpi.first.math.geometry.Pose2d;
import edu.wpi.first.math.geometry.Rotation2d;
import edu.wpi.first.wpilibj.smartdashboard.Field2d;
import edu.wpi.first.wpilibj.smartdashboard.SmartDashboard;
```

#### Step 2: Create Field2d Object

Add a `Field2d` field to your Robot class:

```java
private final Field2d m_field = new Field2d();
```

#### Step 3: Initialize Field2d in Constructor

In your `Robot()` constructor, add the Field2d to SmartDashboard:

```java
SmartDashboard.putData("Field", m_field);
```

#### Step 4: Update Robot Pose in robotPeriodic()

Add a `robotPeriodic()` method to update the robot's pose. For a basic differential drive robot, you can track the pose manually or use odometry. Here's a simple example that tracks position based on motor outputs:

```java
@Override
public void robotPeriodic() {
    // Update robot pose on the field
    // This is a simplified example - in a real robot, you'd use encoders and odometry
    // For now, we'll use a basic pose that updates based on time and motor states
    
    // Get current pose (you'll need to track this properly with odometry)
    Pose2d currentPose = new Pose2d(0, 0, new Rotation2d(0));
    
    // Update the field visualization
    m_field.setRobotPose(currentPose);
}
```

**Note:** For accurate pose tracking, you should use `DifferentialDriveOdometry` with encoder readings. The example above is simplified - in practice, you'll want to:
1. Add encoders to your drivetrain motors
2. Use `DifferentialDriveOdometry` to track the robot's pose
3. Update the odometry in `robotPeriodic()` with encoder values
4. Use `odometry.getPoseMeters()` to get the current pose

### Viewing the Field Visualization

Once you've added the Field2d code, you can view the robot's movement on the field using either SmartDashboard or Shuffleboard.

#### Launching SmartDashboard

SmartDashboard is a simple dashboard tool that displays robot data in a grid layout. Here's how to launch it:

**Method 1: Using VS Code Command Palette**
1. Open VS Code
2. Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux) to open the command palette
3. Type "WPILib: Start Tool" and select it
4. Choose "SmartDashboard" from the list of tools
5. SmartDashboard will open in a new window

**Method 2: Using VS Code WPILib Menu**
1. In VS Code, look for the WPILib icon in the left sidebar (or use the WPILib menu)
2. Click on "WPILib" in the menu bar (if available)
3. Select "Start Tool" → "SmartDashboard"

**Method 3: Using Terminal/Command Line**
1. Open a terminal in your project directory
2. Run: `./gradlew smartDashboard` (or `gradlew.bat smartDashboard` on Windows)
3. SmartDashboard will launch automatically

**Finding the Field Widget in SmartDashboard:**
1. Once SmartDashboard is open, look for a tab or section labeled **"Field"**
2. The Field widget should appear automatically if you've added it with `SmartDashboard.putData("Field", m_field)`
3. If you don't see it, make sure your robot code is running and the simulator is active
4. The Field widget shows a top-down view of the FRC field with your robot's position

#### Launching Shuffleboard

Shuffleboard is a more advanced dashboard tool with customizable layouts. Here's how to launch it:

**Method 1: Using VS Code Command Palette**
1. Open VS Code
2. Press `Cmd+Shift+P` (Mac) or `Ctrl+Shift+P` (Windows/Linux) to open the command palette
3. Type "WPILib: Start Tool" and select it
4. Choose "Shuffleboard" from the list of tools
5. Shuffleboard will open in a new window

**Method 2: Using VS Code WPILib Menu**
1. In VS Code, look for the WPILib icon in the left sidebar (or use the WPILib menu)
2. Click on "WPILib" in the menu bar (if available)
3. Select "Start Tool" → "Shuffleboard"

**Method 3: Using Terminal/Command Line**
1. Open a terminal in your project directory
2. Run: `./gradlew shuffleboard` (or `gradlew.bat shuffleboard` on Windows)
3. Shuffleboard will launch automatically

**Note:** Shuffleboard may also open automatically when you start the simulator, depending on your WPILib configuration.

**Adding the Field Widget in Shuffleboard:**
1. Once Shuffleboard is open, you'll see a default layout
2. Click the **"Add"** button (usually in the top toolbar) to add a new widget
3. In the widget selection dialog, look for **"Field"** or **"Field2d"** in the list
4. Select it and choose where to place it on your layout
5. The Field widget will appear and show your robot's position

**Alternative: Using Shuffleboard's Source Tree**
1. In Shuffleboard, look for the **"Sources"** panel on the left side
2. Expand the tree to find **"Field"** under your robot's data sources
3. Drag the "Field" item onto your dashboard layout
4. It will automatically create a Field widget

#### Viewing Your Robot on the Field

Once you have the Field widget visible in either SmartDashboard or Shuffleboard:

1. **Start the Simulator** (if not already running):
   - In VS Code, use the command palette: "WPILib: Simulate Robot Code"
   - Or use the debug/run configuration

2. **Enable Robot Mode**:
   - In the Simulation GUI, click **"Teleop"** or **"Autonomous"** in the Robot State panel
   - The robot must be in an active mode (not Disabled) for the pose to update

3. **Observe the Robot**:
   - The robot appears as a **small triangle** on the field
   - The triangle's position shows where the robot is on the field
   - The triangle's orientation (which way it points) shows which direction the robot is facing
   - As your robot moves (via joystick input or autonomous code), you'll see it move around the field in real-time

4. **Field Coordinates**:
   - The field uses meters as units
   - (0, 0) is typically at the center or a corner of the field, depending on the field image
   - X-axis typically runs along the length of the field
   - Y-axis typically runs along the width of the field

### Understanding the Field Display

- **Robot Position**: The triangle represents your robot's current position on the field
- **Robot Orientation**: The direction the triangle points shows which way the robot is facing
- **Field Coordinates**: The field uses meters as units, with (0, 0) typically at the center or corner of the field
- **Field Image**: The background shows a standard FRC field layout

### Troubleshooting Field Visualization

**Field widget doesn't appear:**
- Make sure you've added `SmartDashboard.putData("Field", m_field);` in your constructor
- Restart the simulator after adding the Field2d code
- Check that SmartDashboard or Shuffleboard is running

**Robot doesn't move on the field:**
- Verify that `robotPeriodic()` is being called and updating the pose
- Check that you're updating `m_field.setRobotPose()` with a valid `Pose2d`
- Make sure your pose values are changing (not always the same position)

**Robot position is incorrect:**
- If using manual pose tracking, ensure your calculations are correct
- For accurate tracking, implement proper odometry with encoders
- Verify that your coordinate system matches the field orientation

### Advanced: Using Odometry for Accurate Tracking

For accurate robot pose tracking, you should use WPILib's odometry classes:

1. **Add encoders** to your left and right drive motors
2. **Create a `DifferentialDriveOdometry`** object in your Robot class
3. **Initialize odometry** in `robotInit()` or `autonomousInit()` with the starting pose
4. **Update odometry** in `robotPeriodic()` using encoder distances:
   ```java
   odometry.update(gyro.getRotation2d(), leftEncoderDistance, rightEncoderDistance);
   Pose2d currentPose = odometry.getPoseMeters();
   m_field.setRobotPose(currentPose);
   ```

This provides accurate position tracking based on actual wheel movement, which is essential for autonomous navigation.

