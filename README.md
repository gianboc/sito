---
title: COMSOL
layout: home
nav_order: 3
---


# temp-guidacomsol
Repo temporaneo per guida comsol, prima di creazione repo definitivo aperto

# Installation

*TODO: add instruction for installing the license server*

To download and install COMSOL on your machine you just need to follow the next steps:

- Create a COMSOL account (username and password) here: [https://www.comsol.it/access/login](https://www.comsol.it/access/login)
- Access with your account and get the COMSOL version you want: [https://www.comsol.it/product-download](https://www.comsol.it/product-download) (Note: if no selection is made, the last available will be downloaded, v6.1 at time of writing)
- Extract the contents of the compressed folder
- Open a terminal in that folder and run the following command: `./setup`
- A window will open with some steps to follow and some options to choose (for example, it will be asked if the user wants to install the COMSOL guides and manuals)
- Insert the license (this can be done by typing the name of the license server or by manually inserting the `license.dat` file)
- Follow the steps until the installation is completed

# The license

Each COMSOL license is valid for a single graphical user interface (GUI) associated with a user. With user it is meant the username with which you access your workstation or cluster.
For example: the user **abc** (associated with the machine `abc@workstation.polito.it`) will be able to open on their computer only one COMSOL window. If the user **def** (associated with the workstation `def@workstation.polito.it`), who uses the same license as **abc**, tries to open COMSOL on their workstation, it will throw an error.

A single user, on a single workstation, and with the same username, can open all the COMSOL windows they want (only with the FNL license, see below).

To run multiple COMSOL simulations (or run multiple simulations and simultaneously prepare another one using the GUI) it is necessary to use the *batch mode*. To do this, you must follow some rules:


- Have a Floating Network License (FNL)
- Have the same username on the workstations or clusters on which you want to run the simulations

- Launch the simulation runs **before** opening the GUI (if it is necessary) 

Example:

Let's say a COMSOL user wants to launch two simulations and prepare the setup for a third.
They have the following accounts for workstations and clusters, all with the same COMSOL license installed:

- `abc@workstation1.polito.it`
- `abc@workstation2.polito.it`
- `def@workstation1.polito.it`
- `abc@cluster.polito.it`
- `ghi@cluster.polito.it`

The only way to run multiple simulations on different machines is to use the abc account.
It is therefore necessary to launch the simulations in batch on the accounts `abc@cluster.polito.it` and `abc@workstation2.polito.it` and then prepare the setup of the next simulation on the GUI.
Any attempt to open COMSOL (both in batch mode and in GUI mode) on def@workstation1.polito.it or on `ghi@cluster.polito.it` will be inhibited.

# Running simulations
## Simulation in batch mode

To run a simulation in batch mode, you must use the following command:

<!-- create a bash code block -->
```bash
/home/USERNAME/comsol60/multiphysics/bin/comsol 
-usebatchlic batch -np 16 -inputfile input.mph 
-outputfile output.mph
```
Note: the order in which the flags are inserted must be maintained.
More information on the possible targets and options of COMSOL can be found at the following link:
https://doc.comsol.com/5.5/doc/com.comsol.help.comsol/comsol_ref_running.29.30.html
In the case of using COMSOL on a cluster, with a single FNL license, it is possible to request an unlimited number of nodes and/or cores.

## Server-Client
The server-client option of COMSOL allows you to prepare the setup of a simulation on a less powerful computer (client) and then launch the simulation on a machine with more computational resources (server).
In this brief guide the server-client dynamic has not been explored in depth because it was not considered that it could bring great advantages over the classic ssh connection of Linux but it was nevertheless mentioned to clarify the existence of this possibility.
More information can be found at the following link at the COMSOL official website: https://www.comsol.it

## Useful links

Account creation: https://www.comsol.it/access/login

COMSOL download: https://www.comsol.it/product-download

Guides and manuals: https://doc.comsol.com/6.1/docserver/#!/com.comsol.help.comsol/helpdesk/helpdesk.html

Linux commands: https://doc.comsol.com/5.5/doc/com.comsol.help.comsol/comsol_ref_running.29.30.html



# Costs of the license
For the purchase / renewal of COMSOL there are three possibilities:

- Yearly license: base price from list and duration of 12 months
- Perpetual license: base price from list and duration of 12 months, 60\% discount on the base price at renewal
- University license (under negotiation)


|                                 | FNL Annuale | FNL Perpetua |
|---------------------------------|-------------|--------------|
| COMSOL Multiphysics Base        | 1995€ +VAT  | 3990€ +VAT   |
| Battery Design Module           | 995€ +VAT   | 1990€ +VAT   |
| CAD Import Module               | 495€ +VAT   | 990€ +VAT    |
| TOTAL  (1° anno)                | 3485€ +VAT  | 6970€ +VAT   |
| TOTAL  (3 anni)                 | 10455€ +VAT | 9758€ +VAT   |

