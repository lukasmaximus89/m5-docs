# M5StickV Quick Start {docsify-ignore-all}

## CONTENT

**[1. Download Firmware](#Download)**

**[2. Flash Firmware](#Flash)**

**[3. Serial Debugging Tool](#Serial-Tool)**

**[4. Hello World](#Hello-World)**

**[5. Edit and Run the Code](#Edit-and-Run-the-Code)**

**[6. Library](#Library)**



## Download


<a href="https://m5stack.oss-cn-shenzhen.aliyuncs.com/resource/docs/m5stickV_Firmware_0630Fixed.kfpkg"><button type="button" class="btn btn-primary">click to download firmware </button></a>


## Flash

>1. Flash tool Kflash_GUI.

<div class="link">
 <h4><span>Kflash_GUI:</span></h4>
    <p>
    <a href="http://dl.cdn.sipeed.com/kflash_gui_v1.2.5_windows.zip" target="_blank" rel="noopener noreferrer"><img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/files/windows_89cc6ea0-2a3c-4327-97e5-8f51f448c38b_icon.png?v=1557026574" alt="">Windows</a>
    <a href="http://dl.cdn.sipeed.com/kflash_gui_v1.2.5_macOS.dmg" target="_blank" rel="noopener noreferrer"><img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/files/mac_large.png?v=1557026570" alt="">MacOS</a>
    <a href="http://dl.cdn.sipeed.com/kflash_gui_v1.2.5_7_linux.tar.xz" target="_blank" rel="noopener noreferrer"><img src="https://cdn.shopify.com/s/files/1/0056/7689/2250/files/linux_icon.png?v=1557026584" alt="">Linux</a></p>
</div>

>2.Connect the device to your computer via Type-C cable, double click to open up flash tool **Kflash_GUI**, choose the right com number, firmware, bandrate and click download to start it. 

<img src="assets\img\getting_started_pics\m5stickv\kflash_gui_01.jpg">

### Kflash

>3.For people who are used to operate by shell command, you can choose Kfalsh as your firmware falshing tool .[click for more detail](https://github.com/kendryte/kflash.py)


## Serial-Tool

>1. You will need a serial debugging tool for programming M5StickV, you can use Putty [in here](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html),for download and information.

>2. Run Putty, connect M5StickV to your PC, in Putty, set com number, baudrate, click "open", by now the connect process should started.(you can check the com number in device manager on your PC)

<img src="assets\img\getting_started_pics\m5stickv\putty_01.jpg">

> When connected, it will automatically enter Maixpy UI. Now the device is runing the default code, you can terminate it by "Ctrl+C".

<img src="assets\img\getting_started_pics\m5stickv\putty_02.jpg">


## Hello World

>Type in the following code, a display "hello world" will show on the screen .

```
import lcd

lcd.init()
lcd.draw_string(100, 100, "hello world", lcd.RED, lcd.BLACK)

```


## Edit and Run the Code

### Editting


> The language shell programm(REPL) is good for instant code validatation, it can be used at short code programming and validation. In real project where we will have massive amount of code, in that case we will need a Code Editor for better orgnization of the code files.


>Inside MaixPy，integrates a open source Editor [Micropython Editor(pye)](https://github.com/robert-hh/Micropython-Editor)，which is convenient for us to manage the code.

function `os.listdir()`  is for checking the files in current directory.


With function `pye("hello.py")`, you can create new files and enter editing mode(if file exist, only enter editting mode)[click for more](https://github.com/robert-hh/Micropython-Editor/blob/master/Pyboard%20Editor.pdf)

If editing finished, you can do  `Ctrl+S` > `Enter` to save the script. `Ctrl+Q` to exit edit mode.


**Notice**： This editor have some requiremnt on the Serial tool,  KEY `BackSpace` have to set as `DEL` function，or `BackSpace` will implement the same function as  `Ctrl+H`(charater replacement)

### Upload File

> Although inner editor of MaixPy can help us manage the file, for better experience and efficiency we recommend using other editors and upload the project after finish editing.

>[uPyLoader](https://github.com/BetaRavener/uPyLoader) is opensource, which is pretty full-function and gives you the permit to upload, download, file excution, output monitoring, etc. 

<a href="https://github.com/BetaRavener/uPyLoader/releases"><button type="button" class="btn btn-primary">Download uPyLoader</button></a>


### File Execution

Function `os.chdir()` is used for switch current directory to a certain directory, for example `os.chdir("/flash")`

#### Solution 1： `import`

Run  `import hello`

You can see the output: `hello maixpy`

In this way, it is simple and handy, but thers something worth your attention, `import` can only be utilized once, the second time `import` won't work. If you need to use `import` mutiple times, please refers to solution 2 below

#### Solution 2： `exec()`

Use `exec()` function: 

```python
with open("hello.py") as f:
    exec(f.read())

```

### AutoRun after Power On 


System will create a `boot.py` file at directory `/flash` or  `/sd` , it will run this script after power on, modify this file will realize the AutoRun.

## Library


<a href="https://maixpy.sipeed.com/zh/libs/standard/"><button type="button" class="btn btn-primary">get more examples</button></a>



<style>

.link a{

    padding-left: 13%;

}

</style>