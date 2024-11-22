# Unit 1 Overview
## Description
This unit will cover basic software application setup and how the software is used, as well as FRC basics. Some of the software applications required include Github and WPILib. 
## Prerequisites
Basic programming and java knowledge is required, as well as access to an XRP minibot and a computer and Xbox controller if possible.
## What is FRC?

https://github.com/user-attachments/assets/bd031688-271f-4b52-9003-999f6a2680e7<br>
FIRST Robotics Competition (FRC) is a robotics competition where each year, there is a new prompt and competitors have to create a robot for that prompt. A FRC match is made of several parts. <br>
* Autonomous Period – When the robot operates without input from drive team. <br>
* Teleoperated Period – The time when the drive team remotely controls the robots. <br>
## Github
Github is a developer platform used to create, manage, and share code. There are a couple of steps needed to install Github Desktop or Git.

### Installing Git
Git is a command-line tool that will be used to manage the code.<br>

Instructions for downloading Git are located in the following link: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git. Scroll down to the section with instructions for your operating system. Installation may require usage of a command line.
### Installing Github Desktop
Github Desktop is the graphical interface for Git.<br>
 
1. Visit https://github.com/ and sign up for an account
2. Visit https://desktop.github.com/download/
3. Download the application appropriate for your operating system and the latest version (this is often the recommended one).
4. Open the downloaded file and follow instructions
5. Sign in on Github Desktop

 
## WPILib
1. Visit https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html. The file to download and instructions to download are both located here.
2. Scroll down until you see the download button.
3. Install the latest release appropriate for your operating system. 
4. Extract the Installer as shown below the download button in the website for your operating system.
5. Open the installer and press the start button.
6. When prompted to choose the install mode, choose the “everything” mode.
7. To download the VS Code, choose “Download for this computer only”. It is very important that VS Code is installed.
8. Wait for the download to finish and press the finish button.
9. There may be post-installation instructions after the download. Follow the instructions for your operating system from the website.

# Unit 2 Overview
## Description
This unit will introduce software, command line, and XRP hardware concepts. This unit will allow you to run your first XRP minibot program.
## Prerequisites
An XRP minibot is required for this unit.
## Command Line
What is the command line? Command line is a way to interact with a computer program by inputting text commands into a command line application. <br>

What are some of the commands? The commands differ between operating systems. <br>

<b>Windows</b><br>
https://www.youtube.com/watch?v=Df2rx7b2tMY	 <br>
https://www.youtube.com/playlist?list=PL6gx4Cwl9DGDV6SnbINlVUd0o2xT4JbMu <br><br>
<b>MacOS/Linux</b><br>
https://www.youtube.com/watch?v=dWFMRp6KtlQ <br>
https://www.youtube.com/watch?v=2IaB93h9tE0 <br>

## Git Commands
Remember the software we installed for the command-line in Unit 1? That software is called git. Git commands can only be run in command lines.

## Understanding Github 
**Vocabulary**<br>
* Repository – Where the code is stored and files are stored and shared <br>
* Branch – New, separate version of the main repository <br>
   * Main branch – Repository "default" branch
* Clone – Copy repository to local machine <br>
* Fetch – Grab changes from online repository, but do not apply them yet
* Commit – Save your work locally with a description and message <br>
* Pull – Grab changes from the online repo and add them to your files.
* Push – Send changes to the online repo.

## Basic Git Commands
https://www.youtube.com/watch?v=HVsySz-h9r4

## Introduction to Hardware
Each XRP bot comes equipped with…
<details> 
  <summary>A servo</summary>
          Specialized motors with a feedback mechanism.
</details>
<details> 
  <summary>Two drive motors</summary>
          Component that moves the minibot.
</details>
<details> 
  <summary>Range finder</summary>
          Finds distance from an object.
</details>
<details> 
  <summary>Line-finding sensor</summary>
          Helps to find and follow lines.
</details>

## PROJECT: Running the Robot
1. Open Team670’s GitHub and find 2024-Minibots.
2. Clone this repository and open with WPILib VS Code
3.Turn the robot on
4. Connect to the robot’s wifi on your laptop- password should be team670
5. Press Ctrl-Shift-P/Cmd-Shift-P and enter Simulate Robot Code
6. To connect the controller, drag Joysticks[0] to System Joysticks and select teleop.
7. Now, you should be able to manually control your robot.

## Introduction to Software
The robot is controlled by code that you have cloned from the repository. Navigate to the file called AutonomousDistance.java. The path should be XRPminibots/src/main/java/frc/robot/commands/AutonomousDistance.java. <br>

The following is the code in the file.
<br>

```
package frc.robot.commands;


import frc.robot.subsystems.Drivetrain;
import edu.wpi.first.wpilibj2.command.SequentialCommandGroup;


public class AutonomousDistance extends SequentialCommandGroup {
  /**
   * Creates a new Autonomous Drive based on distance. This will drive out for a specified distance,
   * turn around and drive back.
   *
   * @param drivetrain The drivetrain subsystem on which this command will run
   */
  public AutonomousDistance(Drivetrain drivetrain) {
    addCommands(
        new DriveDistance(-2, 20, drivetrain),
        new TurnDegrees(-1, 90, drivetrain),
        new DriveDistance(2, 15, drivetrain),
        new TurnDegrees(5, 45, drivetrain),
        new DriveDistance(1, 10, drivetrain)
    );
  }
}
```

### Understanding FRC Code
The AutonomousDistance class inherits properties from SequentialCommandGroup. <br>

SequentialCommandGroup essentially runs commands in sequential order. Inside the AutonomousDistance class is a constructor with a Drivetrain parameter, or what moves the robot. In the constructor, it uses the method addCommands() and inside, there are many commands which tell the Drivetrain to do specific actions in sequential order.

### Try It Yourself

<details> 
  <summary>Question: Now, try to Simulate the Robot Code, and select the Autonomous mode. What happens?</summary>
           Answer: The robot should more forward and turn automatically. 
</details>

# Unit 3 Overview

## Description
This unit will cover the two subsystems: Arm and DriveTrain, along with commands for the XRP minibot. The project in this unit will allow you to use commands to control the Arm and DriveTrain.

## Prerequisites
An XRP minibot that can successfully connect to your laptop is required for this unit.

## What are the Arm and DriveTrain?
The Arm of the minibot is controlled by a servo in the robot, and the angle can be controlled from 0-180 degrees. The main body of the minibot is called the DriveTrain, because it contains the two wheels that allow the robot to drive. An important thing to note is that the XRP robot turns using skid-steering. While the robot is turning some of the wheels, sometimes the front casters will be skidding. 

## Commands
The GitHub repository with the minibots code includes many existing commands to control the Arm and DriveTrain of the robot. For example, an important command for the minibot is called DriveDistance(), where the robot will drive for a specific distance and speed. 

Types of commands include commands that run initial autonomous movement, drive the robot a certain distance, and turn the robot for a certain number of degrees or seconds. Using these built-in commands, you can move the robot’s drivetrain whichever way you want as long as it’s within the robot’s constraints.

Commands will extend, or inherit from, the Command class. There is also the SequentialCommandGroup.

## PROJECT: Creating a Command for the DriveTrain




