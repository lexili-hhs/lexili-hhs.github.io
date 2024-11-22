# Unit 1 Overview
## Description
This unit will cover basic software application setup and how the software is used, as well as FRC basics. Some of the software applications required include Github and WPILib. 
## Prerequisites
Basic programming and java knowledge is required, as well as access to an XRP minibot and a computer and Xbox controller if possible.
## What is FRC?
FIRST Robotics Competition (FRC) is a robotics competition where each year, there is a new prompt and competitors have to create a robot for that prompt. A FRC match is made of several parts. <br>
Autonomous Period – When the robot operates without input from drive team. <br>
Teleoperated Period – The time when the drive team remotely controls the robots. <br>
## Github
Github is a developer platform used to create, manage, and share code. There are a couple of steps needed to install Github Desktop or Git.

### Installing Git
Git is a command-line tool that will be used to manage the code.<br>

Instructions for downloading Git are located in the following link: https://git-scm.com/book/en/v2/Getting-Started-Installing-Git. Scroll down to the section with instructions for your operating system. Installation may require usage of a command line.
### Installing Github Desktop
Github Desktop is the graphical interface for Git.<br>
 
<ol><li>Visit https://github.com/ and sign up for an account</li>
<li>Visit https://desktop.github.com/download/</li>
<li>Download the application appropriate for your operating system and the latest version (this is often the recommended one).</li>
<li>Open the downloaded file and follow instructions</li>
<li>Sign in on Github Desktop</li>

</ol>
 
## WPILib
<ol>
<li>Visit https://docs.wpilib.org/en/stable/docs/zero-to-robot/step-2/wpilib-setup.html. The file to download and instructions to download are both located here.</li>
<li>Scroll down until you see the download button.</li>
<li>Install the latest release appropriate for your operating system. </li>
<li>Extract the Installer as shown below the download button in the website for your operating system.</li>
<li>Open the installer and press the start button.</li>
<li>When prompted to choose the install mode, choose the “everything” mode.</li>
<li>To download the VS Code, choose “Download for this computer only”. It is very important that VS Code is installed.</li>
<li>Wait for the download to finish and press the finish button.</li>
<li>There may be post-installation instructions after the download. Follow the instructions for your operating system from the website.</li>
</ol>

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
https://www.youtube.com/playlist?list=PL6gx4Cwl9DGDV6SnbINlVUd0o2xT4JbMu <br>
<b>MacOS/Linux</b><br>
https://www.youtube.com/watch?v=dWFMRp6KtlQ <br>
https://www.youtube.com/watch?v=2IaB93h9tE0 <br>

## Git Commands
Remember the software we installed for the command-line in Unit 1? That software is called git. Git commands can only be run in command lines.

## Understanding Github 
Vocabulary<br>
Repository – Where the code is stored and files are stored and shared.<br>
Branch – New, separate version of the main repository.<br>
Main branch/Master branch<br>
Clone – <br>
Commit – <br>

## Basic Git Commands
https://www.youtube.com/watch?v=HVsySz-h9r4

## Introduction to Hardware
Each XRP bot comes equipped with…
<ul><li>A servo</li>
<li>Two drive motors</li>
<li>A range finder</li>
<li>Line-finding sensor</li></ul>

## PROJECT: Running the Robot
<ol><li>Open Team670’s GitHub and find 2024-Minibots. </li>
<li>Clone this repository and open with WPILib VS code</li>
<li>Turn the robot on</li>
<li>Connect to the robot’s wifi on your laptop- password should be team670</li>
<li>Press Ctrl-Shift-P/Cmd-Shift-P and enter Simulate Robot Code</li>
<li>To connect the controller, drag Joysticks[0] to System Joysticks and select teleop.</li>
<li>Now, you should be able to manually control your robot.</li></ol>


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

## Understanding FRC Code
The AutonomousDistance class inherits properties from SequentialCommandGroup. <br>
SequentialCommandGroup essentially runs commands in sequential order. Inside the AutonomousDistance class is a constructor with a Drivetrain parameter, or what moves the robot. In the constructor, it uses the method addCommands() and inside, there are many commands which tell the Drivetrain to do specific actions in sequential order.

### Try It Yourself
Now, try to Simulate the Robot Code, and select the Autonomous mode. What happens?
