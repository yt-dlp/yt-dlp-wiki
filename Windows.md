# How do I run yt-dlp on Windows?

## Quick Setup for Beginners

1. [Download ](https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp.exe)

2. Open File Explorer. Create a new folder in your Downloads folder called YT-DLP

3. Cut & paste or drag & drop the file yt-dlp.exe into the new folder

4. Whenever you want to use yt-dlp, open this folder in File Explorer. Shift + right click the file 'yt-dlp.exe' and choose ```Open Powershell Window Here``` or ```Open Command Prompt Window Here```. Click on it.

5. Test that it is working by typing ```.\yt-dlp -h```. This runs the program and displays the help information. 
 
6. Now, type ```.\yt-dlp "<url>"```, replacing ```"<url>"``` with the web address of a youtube video inside "" quotation marks. Press enter.

7. Your files will download into the folder YT-DLP

8. In future, you can add extra instructions for how a video downloads. The options are listed in README.Md. Just type extra options onto the end of your line. For example, to download a video as an mp3 music file: 

```.\yt-dlp "<url>" -x --audio-format mp3```

## For long term use

The quick setup has two downsides. You can only download files to one specific folder, and you must remember to type ".\yt-dlp" each time. 

The way you have learned depends on Windows knowing exactly which folder the .exe is in and which folder the user is in. If you add the program to your PATH, Windows will be able to access the program from any location - like looking it up on a map.

1. Open the command prompt as administrator. Click Start, type cmd. When the cmd.exe icon appears, right click and select "Run as administrator".

2. Go to File Explorer and open the folder where yt-dlp.exe is saved. File Explorer has a 'url bar' - click in the white space of the bar to see the folder URL. Copy it. 

3. To add/update system environment variables, type this and press Enter: ```setx /m PATH "%PATH%;C:\Downloads\YT-DLP"```. You must replace ```C:\Downloads\YT-DLP``` with the folder url saved in the last step}

You can now go to any folder on File Explorer, shift+right click and choose 'Open Command Window Here'. Then, you can type ```yt-dlp "<url>"``` to download files to this folder. 

## Using a GUI

A GUI is a 'graphical user interface' - instead of typing in the command prompt, a program window pops up like any other app on your computer. There are several options available, but they are not being developed by this project directly, so you must do your own research about which are available, up to date, and best meet your needs. 




