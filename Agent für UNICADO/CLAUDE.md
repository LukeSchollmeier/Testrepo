# Project Context

This is my AI Agent, that assists me in conceptual aircraft design, using the UNICADO workflow. The UNICADO Workflow contains several different modules, which perform calculations for the conceptual aircraft design (e.g. aerodynmics, initial sizing, etc.). These modules are executed in a certain sequence, which is controlled in the Remote Component Enviroment (RCE).

# About Me

I am an engineer, who wants to perform conceptual aircraft design within the UNICADO Workflow.

# Rules

- Always ask clarifying questions before starting complex tasks
- Show your plan and steps before executing
- When you're asked (or decide yourself) to execute the UNICADO Workflow follow the "Instructions for executing the UNICADO Workflow" below 

# Operating System and Terminals
- The opertaing system is windows. 
- Use PowerShell for executing .exe files 
- Use Git-Bash for the tail command

## Don't read unnessecary files 
- Do NOT read internal files from RCE (Plugins, JARs, Konfigurationen)
- You'll only need: rce.exe and the .wf Workflow-file
- Ask me, if you don't find a path
- Don't read unnessecary files 

# Instructions for executing the UNICADO Workflow
To execute the UNICADO workflow, follow the steps below. 

## Step 1: 
Open the events-compact.log file by using the following Bash-Command in Git Bash: tail -f "C:/Users/lukeb/.rce/default/events-compact.log"

## Step 2:
Have a look in the following folder: "C:\Programs\UNICADOworkflow\workflowResults"

## Step 3:
PowerShell Commands — execute exactly like instructed
Step 1:
cd "C:\Program Files\RCE\rce"

Step 2 — NOT in backround, NOT as backround process:
.\rce.exe --headless --batch "wf run C:\Programs\UNICADOworkflow\workingDirectoryRCE\UNICADOworkflow\UNICADOworkflow.wf"

IMPORTANT: run_in_background must be FALSE 
IMPORTANT: Timeout must be at least 900000ms (15 Minuten)
IMPORTANT: Wait until the command is fully completed

## Step 4:
Monitor the events-compact.log file.
Check for the follwoing lines to appear:
- "application.starting"
- "network.node.named"
- "sysmon.initialized"
- "workflow.execution.requested"
- "workflow.request.initiated"

Wait while the UNICADO Workflow runs. This can take up to 900 seconds. If the UNICADO Workflow is finished the "application.terminating" line will appear. 

If all lines appeared, the workflow should be executed and you can go to the next step - do NOT start it earlier. 
If NOT all lines appeared, report the status: "Executing Workflow failed!" and wait for instructions.

## Step 5:
Look in the folder "C:\Programs\UNICADOworkflow\workflowResults" again and check if there is a new folder. The name should contain UNICADOworkflow and the date and time of the execution. 

If there is a new folder with an appropriate name, report the status: "Executing Workflow succeeded!" and wait for new instructions. 
If there is NOT a new folder or the name of the folder contains "Failed_execution", report the status: "Executing Workflow failed!" and wait for instructions.






