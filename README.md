# pico
Learning PiPico

## Docucment Link
datasheets.raspberrypi.com/pico/getting-started-with-pico.pdf

## Clone PICO SDK
cd ~
git clone https://github.com/raspberrypi/pico-sdk.git --branch master
cd pico-sdk
git submodule update --init

## Clone PICO Examples
cd ~
git clone https://github.com/raspberrypi/pico-examples.git --branch master
cd pico-examples
git submodule update --init

## Clone PICO Playground
cd ~
git clone https://github.com/raspberrypi/pico-playground.git --branch master
cd pico-examples
git submodule update --init


## Clone PICO Extras
cd ~
git clone https://github.com/raspberrypi/pico-extras.git --branch master
cd pico-examples
git submodule update --init

## Update Bashrc
add to end of .bashrc

export PICO_SDK_PATH=/home/yash/pico-sdk
export PICO_EXAMPLES_PATH=/home/yash/pico-examples
export PICO_EXTRAS_PATH=/home/yash/pico-extras
export PICO_PLAYGROUND_PATH=/home/yash/pico-playground

source ~/.bashrc

## Installing Toolchain
>> followed on ubuntu 22.04

sudo apt update
sudo apt install cmake gcc-arm-none-eabi libnewlib-arm-none-eabi build-essential

## Building Pico-Examples
cd ~/pico-examples
mkdir build
cd build

>> this will generate all the make files
cmake ..

cd blink
make -j4
.uf2 file will be generated

## Flash on blink.uf2 on board
Press the bootsel button and insert the usb cable.(ie. board powered off initially)
Drag and drop the executable and it sould start blinking.

## Build and Flash other examples
cd ~
cd ~/pico-examples/build/hello_world
make -j4
cd hello_usb

Flash ~/pico-examples/build/hello_world/usb/hello_usb.uf2 on board.
dmesg to find the com port: ttyUSBACM0

sudo minicom -D /dev/ttyACM0 -b 115200
You will see hello world printed:

Welcome to minicom 2.8

OPTIONS: I18n 
Port /dev/ttyACM0, 23:32:41

Press CTRL-A Z for help on special keys

Hello, world!
Hello, world!


