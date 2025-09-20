# 🔧 Installation Guide
This document lists the installation steps for all the tools required in the **VSD RISC-V SoC Tapeout Program**.

# System Requirements
* OS: Ubuntu 20.04+
* RAM: 6 GB
* Disk: 50 GB
* CPU: 4 cores

# Tools Installed
- Yosys (Synthesis)
- Icarus Verilog (Simulation)
- GTKWave (Waveform Viewer)
- Ngspice (Analog Simulation)
- Magic (Layout)
- OpenLANE (PDK + Flow)

# Installation Steps
## 1. Yosys (Synthesis Tool)
```bash
 sudo apt-get update
```
![WhatsApp Image 2025-09-20 at 17 23 46_8e1c1372](https://github.com/user-attachments/assets/aca8fefc-721f-4938-b392-bb7ea7a6c498)
<img width="714" height="435" alt="image" src="https://github.com/user-attachments/assets/ac3cbd63-885e-4d57-b90c-c0ce1b33583b" />

```bash
sudo apt install git
```
<img width="724" height="370" alt="image" src="https://github.com/user-attachments/assets/5042766c-4fc3-4447-864e-808d20983ffe" />

```bash
 git clone https://github.com/YosysHQ/yosys.git
```
<img width="724" height="175" alt="image" src="https://github.com/user-attachments/assets/640f2125-440f-4f2c-ab44-d64be863eb8f" />

```bash
cd yosys
```
<img width="360" height="37" alt="image" src="https://github.com/user-attachments/assets/a9b14fec-2577-4276-aa70-cc5ca9e2029d" />

```bash
 sudo apt install make
```
<img width="677" height="133" alt="image" src="https://github.com/user-attachments/assets/0cedd055-8352-4284-a6c6-b3a4a8611706" />

```bash
 sudo apt-get install build-essential clang bison flex \ 
libreadline-dev gawk tcl-dev libffi-dev git \ 
graphviz xdot pkg-config python3 libboost-system-dev \ 
libboost-python-dev libboost-filesystem-dev zlib1g-dev
```
<img width="718" height="218" alt="image" src="https://github.com/user-attachments/assets/239772ee-3461-47be-9b3e-5d783efe94c2" /> \
If you see `E: Unable to locate package` for `libreadline-dev`, `libboost-python-dev` or `graphviz`, just install them individually
```bash
sudo apt install libreadline-dev
```
<img width="718" height="487" alt="image" src="https://github.com/user-attachments/assets/e68ae7b3-e127-4dd7-97d1-e74cbdea14e4" />
<img width="718" height="436" alt="image" src="https://github.com/user-attachments/assets/70968f68-803b-447e-a45d-f40998eb6a14" />

```bash
sudo apt install graphviz
```
<img width="718" height="350" alt="image" src="https://github.com/user-attachments/assets/a5c525b4-4350-46ec-a2f8-c451a7ef7439" />
<img width="718" height="472" alt="image" src="https://github.com/user-attachments/assets/f170452f-a010-4343-98af-8fba25c8b2ae" />

```bash
sudo apt install libboost-python-dev
```
<img width="718" height="487" alt="image" src="https://github.com/user-attachments/assets/b94e9a6a-e2fd-44b8-a113-a34fcc9c9c33" />
<img width="718" height="471" alt="image" src="https://github.com/user-attachments/assets/445e5833-2cc5-4404-9820-7f0ae1c9fa45" />

Install `pkg-config` depending on your Linux distro:
```bash
sudo apt install pkg-config
```
<img width="714" height="435" alt="image" src="https://github.com/user-attachments/assets/b07c1d50-55cb-4328-b21f-8d7dd83e00a1" />

<img width="714" height="435" alt="image" src="https://github.com/user-attachments/assets/2ea4ce4a-df79-4042-8a81-1761346f273e" />

```bash
make config-gcc
```
<img width="714" height="453" alt="image" src="https://github.com/user-attachments/assets/afb62ed8-f4b6-45cd-ab5a-5a57bd101ea8" />
<img width="714" height="489" alt="image" src="https://github.com/user-attachments/assets/f1de2e0c-58bd-4360-8ece-f1c5255bf49b" />
<img width="714" height="489" alt="image" src="https://github.com/user-attachments/assets/3d40d077-6693-46f6-925a-fdad39767e8c" /> 

Initialize and update all submodules:
```bash
 git submodule update --init --recursive
```
<img width="714" height="174" alt="image" src="https://github.com/user-attachments/assets/5762cc42-054c-4c2c-b2ea-54d4dbeda31b" />

```bash
make -j$(nproc)
```
<img width="727" height="466" alt="image" src="https://github.com/user-attachments/assets/58c76387-403a-41d8-911f-7622fbdbe582" />
<img width="727" height="501" alt="image" src="https://github.com/user-attachments/assets/f732668b-a643-4a9d-8023-49151c61eaca" />
<img width="420" height="91" alt="image" src="https://github.com/user-attachments/assets/0794565e-48a0-4b6d-86a4-0da5dd204dab" />

```bash
 sudo make install
```
<img width="727" height="220" alt="image" src="https://github.com/user-attachments/assets/cfd444f2-2d5f-4ff5-9967-1ed47ec8d036" />

verify
```bash
yosys -V
```
<img width="727" height="45" alt="image" src="https://github.com/user-attachments/assets/869efe94-fa4d-479f-a2ab-5eb3b6381e63" />

## 2. Icarus Verilog (Simulation)
```bash
sudo apt-get update
```
<img width="713" height="507" alt="image" src="https://github.com/user-attachments/assets/80ad2b40-359c-4e1d-b230-f211ee34ff02" />
<img width="713" height="507" alt="image" src="https://github.com/user-attachments/assets/762a8fcc-37bf-46f9-9902-b68151ea9d5a" />

```bash
sudo apt-get install iverilog
```
<img width="713" height="372" alt="image" src="https://github.com/user-attachments/assets/dd7ee0a2-45a3-4d36-ac10-bd4838e2f0e4" />

## 3. GTKWave (Waveform Viewer)
```bash
sudo apt-get update
```
<img width="713" height="507" alt="image" src="https://github.com/user-attachments/assets/80ad2b40-359c-4e1d-b230-f211ee34ff02" />
<img width="713" height="507" alt="image" src="https://github.com/user-attachments/assets/762a8fcc-37bf-46f9-9902-b68151ea9d5a" />

```bash
sudo apt install gtkwave
```
<img width="716" height="510" alt="image" src="https://github.com/user-attachments/assets/296336c5-34bb-44b4-9d42-397afdcd0ed2" />
<img width="716" height="478" alt="image" src="https://github.com/user-attachments/assets/a51bf255-4e30-4557-b92c-952155d0f2bb" />

## 4. Ngspice (Analog Simulation)
 Download Ngspice Source
 ```bash
wget -O ngspice-45.2.tar.gz https://sourceforge.net/projects/ngspice/files/ng-spice-rework/45.2/ngspice-45.2.tar.gz/download
```
<img width="716" height="511" alt="image" src="https://github.com/user-attachments/assets/08bced0b-94f2-478e-8892-9ab5ae968537" />
<img width="716" height="511" alt="image" src="https://github.com/user-attachments/assets/838fb29a-a43b-46ff-8dd6-b7e66a165ba8" />

```bash
 tar -zxvf ngspice-37.tar.gz
```
<img width="716" height="511" alt="image" src="https://github.com/user-attachments/assets/b14e53a2-7573-40de-8dd3-9532ccae9cc5" />
<img width="716" height="511" alt="image" src="https://github.com/user-attachments/assets/02c97417-70e4-4162-a416-7f5a3fdd5475" />

```bash
cd ngspice-37
```
<img width="448" height="46" alt="image" src="https://github.com/user-attachments/assets/2e80572e-6e13-4f40-9cac-776f46daeae9" />

```bash
mkdir release
cd release
```
<img width="448" height="95" alt="image" src="https://github.com/user-attachments/assets/71e4ca5b-e2d3-4b83-9e3d-c3448e9e23ea" />

```bash
../configure  --with-x --with-readline=yes --disable-debug
```
<img width="712" height="471" alt="image" src="https://github.com/user-attachments/assets/9fdfd65e-0ded-4a49-8ccc-6b1802ec8e14" />
<img width="712" height="471" alt="image" src="https://github.com/user-attachments/assets/62b8ab70-553a-43c4-bdde-61a57309ae92" />

```bash
make -j$(nproc)
```
<img width="712" height="471" alt="image" src="https://github.com/user-attachments/assets/21bfab48-7b61-41b8-bfcf-6151985f417d" />
<img width="712" height="471" alt="image" src="https://github.com/user-attachments/assets/7dd09e5d-9336-4fd9-8444-ca29a830315a" />
<img width="712" height="471" alt="image" src="https://github.com/user-attachments/assets/f23f38ed-30fa-495b-a99a-e8af4e5b1cf5" />

```bash
 sudo make install
```
<img width="712" height="502" alt="image" src="https://github.com/user-attachments/assets/db0335de-e974-4427-8cbf-34b3c66d8f97" />
<img width="712" height="517" alt="image" src="https://github.com/user-attachments/assets/eca0c143-febb-4292-a5eb-b3183bd6a365" />

## 5. Magic (Layout)
```bash
  sudo apt-get install m4
  sudo apt-get install tcsh
```
<img width="618" height="150" alt="image" src="https://github.com/user-attachments/assets/b996f182-015c-4b87-aaf6-7cf215ec1adb" />
<img width="717" height="357" alt="image" src="https://github.com/user-attachments/assets/65b45f7b-10be-4342-8f0e-3065019e1565" />

```bash
sudo apt-get install csh
```
<img width="717" height="357" alt="image" src="https://github.com/user-attachments/assets/3753939d-2a35-4ad7-a2c7-d09f6c97aa8e" />

```bash
 sudo apt-get install libx11-dev
```
<img width="717" height="458" alt="image" src="https://github.com/user-attachments/assets/be20101b-f95b-420a-a8c5-e1ade20946f8" />

```bash
sudo apt-get install tcl-dev tk-dev
```
<img width="717" height="458" alt="image" src="https://github.com/user-attachments/assets/314f3602-f5db-43ce-9e08-b14c4618fb3b" />

```bash
sudo apt-get install libcairo2-dev
```
<img width="717" height="409" alt="image" src="https://github.com/user-attachments/assets/be8425e1-8920-4886-9422-9473b97a1ee0" />

```bash
 sudo apt-get install mesa-common-dev libglu1-mesa-dev
 sudo apt-get install libncurses-dev
```
<img width="717" height="409" alt="image" src="https://github.com/user-attachments/assets/d3de94fd-3d7b-4ccb-b4db-a0c29b04821c" />
<img width="717" height="125" alt="image" src="https://github.com/user-attachments/assets/ad651b00-86d4-4bf0-8c8b-f53fe482e44b" />

 Clone Magic Repository
 ```bash
git clone https://github.com/RTimothyEdwards/magic
```
<img width="717" height="181" alt="image" src="https://github.com/user-attachments/assets/94bbbc22-cdc3-4bbd-aa2e-494390f5984f" />

```bash
cd magic
```
<img width="717" height="53" alt="image" src="https://github.com/user-attachments/assets/1be1af9c-8c36-4767-8dd0-15392ec5446e" />

```bash
./configure
```
<img width="717" height="395" alt="image" src="https://github.com/user-attachments/assets/4a30fe5b-b3cf-4e69-ab73-34a6d4c5b7f7" />
<img width="717" height="487" alt="image" src="https://github.com/user-attachments/assets/72b6d798-ffda-4a42-9c72-e7528402ed0f" />

```bash
make
```
<img width="717" height="487" alt="image" src="https://github.com/user-attachments/assets/a1cdf1da-1664-46e6-9131-9c8697f6f015" />
<img width="717" height="509" alt="image" src="https://github.com/user-attachments/assets/ca95d413-6c42-467b-b0d5-5c8aad31070b" />

```bash
sudo make install
```
<img width="717" height="440" alt="image" src="https://github.com/user-attachments/assets/dbe0fb52-b290-474a-b958-cdfbde6d59f8" />
<img width="717" height="440" alt="image" src="https://github.com/user-attachments/assets/e387b32a-f813-4d08-a6fc-995f05d22c13" />

# 6. OpenLANE (PDK + Flow)
```bash
sudo apt-get update 
sudo apt-get upgrade
```
<img width="691" height="499" alt="image" src="https://github.com/user-attachments/assets/7ad39ea3-827e-45f9-bcc2-55713c28ef89" />
<img width="691" height="499" alt="image" src="https://github.com/user-attachments/assets/1a007d95-d844-4493-919b-0c089d89c5f0" />

```bash
sudo apt install -y build-essential python3 python3-venv python3-pip make git
```
<img width="715" height="499" alt="image" src="https://github.com/user-attachments/assets/5e6671e3-18e9-4f6a-9145-688b059e1f2d" />
<img width="715" height="499" alt="image" src="https://github.com/user-attachments/assets/d0ab67c3-8020-4038-a283-e86b617dbd68" />

```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
<img width="715" height="473" alt="image" src="https://github.com/user-attachments/assets/a585a58d-fdb6-4fde-bb99-315ecdb60fde" />
<img width="715" height="473" alt="image" src="https://github.com/user-attachments/assets/2a0e58af-5f84-439a-bc5b-4a02fc4951a2" />

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
<img width="715" height="88" alt="image" src="https://github.com/user-attachments/assets/51dccc85-a8a8-456b-860c-166d3b81f0c4" />
<img width="715" height="88" alt="image" src="https://github.com/user-attachments/assets/b62c6354-a647-4126-9592-9caec7809a10" />

Install Docker
```bash
