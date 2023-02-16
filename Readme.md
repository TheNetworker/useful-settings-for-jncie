[TOC]

# Introduction

The goal of this document is to collect different application settings that you will use during taking your JNCIE-X Exam to have a pleasant and uninterrupted experience. The last thing that you want to see while taking exam is a Screen of Death :(

![How to fix a blue screen of death error in Windows 10 | IT PRO](assets/blue_screen_of_death.png)



or, worse, A notification to restart your laptop to apply unnecessary windows updates!

![Registry Tweak to Force Automatic Restart in Windows 8 After Installing Important  Updates – AskVG](assets/Windows_Update_15_Minutes_Countdown.png)

in this document, You will see different optimization settings for exam applications such as Windows, SecureCRT, and Notepad++. At first glance, you will feel this is a long list to do. However, Remember, you need to do it only a single time for something like `Windows Settings`. In other settings, you need to do them a couple of times and they will be saved in your muscle memory.

# Windows Settings

Below are some settings to tweak the Microsoft `Windows 10` or Microsoft `Windows 11`

## Firewall and Security Settings

- Disable Virus and Malware protection since this service consumes high CPU

![image-20230216154312855](assets/image-20230216154312855.png)



- Disable Microsoft Bitdefender

```shell
run command line as administrator then execute the following command 

REG ADD "hklm\software\policies\microsoft\windows defender" /v DisableAntiSpyware /t REG_DWORD /d 1 /f
```



- Turn any info notifications related to  Windows Security

![image-20230216154539111](assets/image-20230216154539111.png)

## Search and Storage Settings

- Disable Windows Search Service

![image-20230216154402625](assets/image-20230216154402625.png)



- Also, Disable the indexing services for your directories

  ![image-20230216154450621](assets/image-20230216154450621.png)



- Remove Temp files

![image-20230216154610550](assets/image-20230216154610550.png)



- Enable `Storage Sense` to git rid of temp files quickly

![](assets/image-20230209174958025.png)

## Services Settings

- Ensure the background settings are disabled

![image-20230209173133761](assets/image-20230209173133761.png)



- Turn off the `Game Mode`

  ![image-20230209173921796](assets/image-20230209173921796.png)



- Also, Turn off the xbox game bar

![image-20230216154658573](assets/image-20230216154658573.png)

- Disable Cortana

![image-20230216154731552](assets/image-20230216154731552.png)

- Turn off the Bitlocker

![image-20230209174218392](assets/image-20230209174218392.png)



- Disable the transparency and animations under visual effects

![image-20230216154805351](assets/image-20230216154805351.png)



- Ensure the US keyboard is added beside your native language

![image-20230209175133976](assets/image-20230209175133976.png)

> if you're unable to add the US keyboard and you keep getting the UK layout instead, then follow the instructions in this link: https://superuser.com/questions/1429636/how-to-remove-unneeded-eng-international-keyboard-layout-from-windows-10-permane



- Ensure the `US` keyboard layout is selected. Otherwise, the `#` (shift + 3) won't work as expected

![image-20230216154853681](assets/image-20230216154853681.png)



## Windows Update settings

- Update to the latest update available by Microsoft and do all needed restarts

![image-20230216154916335](assets/image-20230216154916335.png) 



- Then pause the updates to the time after your exam (7 days, for example)

![image-20230216154940692](assets/image-20230216154940692.png)



## Battery and Sleep Settings

- Ensure the battery power mode  is `Best Performance`

  ![image-20230216155008561](assets/image-20230216155008561.png)



- Ensure your laptop never go to sleep mode (either when plugged in or connected to a power source) --> This is to avoid disconnecting from the JNCIE exam while taking a break

![image-20230216155027246](assets/image-20230216155027246.png)



## Misc. Settings

- if you're connected to the internet using the ethernet cable, ensure the `Ethernet` icon is showing connected 

![image-20230216155101239](assets/image-20230216155101239.png)



- Turn off windows HotKeys to avoid being triggered during the exam

![image-20230216155121565](assets/image-20230216155121565.png)



- if you're connecting external display, then make sure to select it as your main display and choose `Extend these displays` option

![image-20230216155138428](assets/image-20230216155138428.png)



- Also, make sure the Audio output is coming from your laptop/speakers and not from the display itself

  ![image-20230216155223154](assets/image-20230216155223154.png)





# SecureCRT Settings

As you already know, SecureCRT is the official terminal for JNCIE exams. You will get a licensed version of SecureCRT 8.5 running over Windows VM (different than your windows operating system running on your laptop). Below are a few settings needed to be adjusted on the SecureCRT instance 



## Editing the Global Options

- Configure your preferred `ANSI Color` from `Edit > Global Options > Terminal > Appearance > ANSI Color`

  ![image-20230216155256780](assets/image-20230216155256780.png)

​		



- Also, Do the same in `Advanced > Color schemes`

  ![image-20230216155401367](assets/image-20230216155401367.png)

​	



- Make it easy to clone the current session to another tab by `double click` on the active session. Also, Avoid losing the current open sessions when accidentally clicking on the close session 

  ![image-20230216155418020](assets/image-20230216155418020.png)



- Disable the `Session Zooming` using the mouse

  ![image-20230216155457099](assets/image-20230216155457099.png)

## Editing the Default Sessions

You can access the default session options from `Edit > Edit Default Session`

- Disable the `Jump Scroll` under `Terminal` (This setting used to jump to the last line of the output returned from the remote host. it's distracting when you want to examine a log entries example). Also, Configure the `NO-OP`protocol to be low number (20 seconds for example) to prevent disconnecting the session due to inactivity

  ![image-20230216155520412](assets/image-20230216155520412.png)



- Configure the default Terminal emulation to be `XTERM` with the support of the ANSI color that you previously configured in Global options. Also, increase the `Scrollback Buffer` to the maximum (128000), so you can examine long output without being overwritten

  ![image-20230216155550824](assets/image-20230216155550824.png)



- uncheck the `80/132 column switching` under `Emulation > Modes`. This setting will keep resizing your main SecureCRT window when you enter to a tmux session which is very annoying.

  ![image-20230216155618664](assets/image-20230216155618664.png)



- Check `Ignore window title change requests` under `Emulation > Advanced`. This will force SecureCRT to keep the session name as the hostname (for example `k8s-controller-1`) and not change it to the name of the current directory (i.e. `root@host:/etc/contrail`)

  ![image-20230216155637441](assets/image-20230216155637441.png)



- Again, You can force using a specific look and feel on all sessions by copying the `Current color scheme` into a new name and then configuring the foreground/background color 

  ![image-20230216155705835](assets/image-20230216155705835.png)



- The `jncie` theme for example, is copied from `invisibone` with slight change in background color

  ![image-20230216155726357](assets/image-20230216155726357.png)

​		

- one of the important points, is to configure the `Highlight keywords` in SecureCRT default sessions to match for specific patterns using regex. I used to match IP addresses, states like `UP`, `RUNNING`, `down`, `ERROR`..etc

  ![](assets/image-20230209194752156.png)



- Example of bgp summary after applying the keyword highlighting

  ![image-20230209195611551](assets/image-20230209195611551.png)



# Notepad++ Editor 

The N++ is installed by default on your remote windows session. below are the most important settings in the editor. There are two locations to modify the settings. The `Preferences` and the `Style Configurator`



## Preferences

This settings is accessible from `Settings > Preferences`

- Under `General`, Enable `Multi-line`  to have multiline opened tabs. Also, Enable `Double click to close document` option to save time 

  ![image-20230214193932596](assets/image-20230214193932596.png)



- Under `Language`, Ensure the default `Tab Settings` is set to `2` and the N++ will replace the tab with the white space. This is very important while editing the YAML file. You can also confirm that YAML language will inherit this settings from the default

  ![image-20230214194533077](assets/image-20230214194533077.png)

  ![image-20230214194856299](assets/image-20230214194856299.png)





- Under `Highlighting`, Enable `Highlight Matching Tags` and `Match case` so you can easy find all matching keywords within a file

  ![image-20230214195116102](assets/image-20230214195116102.png)



- Under `Auto-Completion`, Disable it!. Yes you are not developing or writing a code in JNCIE-X exams and this feature is very annoying when you type in the editor.

  ![image-20230214195403113](assets/image-20230214195403113.png)



## Style Configurator

All important options under this setting are located under `Global Styles`. You can access it by going to `Settings > Style Configurator` then applying the following 

- Change the theme to one that is easy on your eye (I feel comfortable with `Solarized-light`)

- increase the `Font size` to 11 or 12, then make this setting applied to all language by selecting `Enable global fount size`

  ![image-20230214195804375](assets/image-20230214195804375.png)

