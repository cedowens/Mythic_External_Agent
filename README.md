# Mythic External Agent

This repo defines the folder structure for an external Mythic agent that can be remotely "installed" into a Mythic instance. This process allows users to create their own Mythic agents and host them on their own GitHub repositories while also allowing an easy process to install agents.

## How to use this git project

This project is a template for what _your_ git-based repository should look like. Simply copy/fork this project and update it with your agent's information. Then, you can use the corresponding install script from within the Mythic repo to install this agent. The Mythic install script for 3rd party agents should work for any git-based repository (GitHub, GitLab, Bitbucket, etc).

## Folder Structure

### Payload_Type

This folder should contain exactly what you have in your `Payload_Types` folder for Mythic. Specifically, it should contain one folder with the same name as your agent. 

Example: https://github.com/its-a-feature/Mythic/tree/master/Payload_Types

### C2_Profiles

This folder should contain exactly what you have in your `C2_Profiles` folder if you added a new C2 Profile for your agent. Specifically, it should containe a folder with the name of the C2 Profile for every C2 Profile you added. If you have no additional C2 Profiles, leave this folder empty.

Example: https://github.com/its-a-feature/Mythic/tree/master/C2_Profiles

### documentation-c2

This folder contains all of the contents for the documentation-docker container that petains to your new C2 profiles (if any). If you have no extra documentation, then leave this folder empty.

Example: https://github.com/its-a-feature/Mythic/tree/master/documentation-docker/content/C2%20Profiles

### documentation-payload

This folder contains all of the contents for the documentation-docker container that pertains to your new payload type. If you have no documentation (you reall should though), then leave this folder empty.

Example: https://github.com/its-a-feature/Mythic/tree/master/documentation-docker/content/Agents 

### documentation-wrapper

If you are creating any "wrapper" style payload types, the documentation for those go in a slightly different location with a slightly different format. Wrapper payload types don't have any C2 or commands associated with them; instead, they take in another agent and "wrap" it with a more generic mechanism (service executable, office macro, obfuscation, etc). While the wrapper payload type code goes into the same Payload_Type area, the documentation is broken out. Copy that documentation here similar to:

https://github.com/its-a-feature/Mythic/tree/master/documentation-docker/content/Wrappers

### agent_icons

This folder contains the svg icons that should be used for the agent. This svg icon is used on the Payload Types page, on the active callbacks page, and when viewing the graph/tree modes of your callbacks.

## Config.json

This file configures which components to ignore on the install process.

### exclude_payload_type

Setting this value to `true` means that after cloning down the remote repository, the installer program will _NOT_ copy the contents of the `Payload_Type` folder into the local `Payload_Types` folder. This is helpful for when an agent's Payload Type contents needs to be installed on a specific computer/VM and _not_ used as part of a Docker deployment.

### exclude_c2_profiles

Setting this value to `true` means that after cloning down the remote repository, the installer program wil _NOT_ copy the contents of the `C2_Profiles` folder into the local `C2_Profiles` folder. This is helpful for when an agent's C2 Profiles might need to run on a different Computer/VM and _not_ used as part of a Docker deployment locally to Mythic.

### exclude_documentation_payload

Setting this value to `true` will prevent Mythic from copying the contents into the documentation-docker's agent folders.

### exclude_documentation_c2

Setting this value to `true` will prevent Mythic from copying the contents into the documentation-docker's c2 folders.

### exclude_agent_icons

Setting this value to `true` will prevent Mythic from copying the contents into the mythic-docker/app/static folder with the other icons.
