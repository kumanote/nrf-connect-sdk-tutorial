[nRF Connect SDKでZephyr RTOSに入門](https://blog.kumano-te.com/activities/introduction-zephyr-rtos-by-ncs)

# Setup

```bash
# python venvを作成＆westインストール
$ pyenv install 3.12.2
$ pyenv virtualenv 3.12.2 nrf_connect_sdk_tutorial
$ pyenv local nrf_connect_sdk_tutorial
$ pip install --upgrade pip
$ pip install west

$ cd app
$ west init -l .
# 以下実行すると、nrf connect sdkやzephyrのgit cloneが走るためかなり時間がかかります。
$ west update
$ west zephyr-export
$ cd ..
$ pip install -r zephyr/scripts/requirements.txt
$ pip install -r nrf/scripts/requirements.txt
$ pip install -r bootloader/mcuboot/scripts/requirements.txt
```

# Build

```bash
$ cd app
# 今回はnRF5340 DKのボード向けにコンパイルする必要がありますので、--boardオプションに指定します。
$ west build --board nrf5340dk_nrf5340_cpuapp_ns
```

# Deploy

```bash
# west flashコマンドを実行すると、ボードに書き込まれてLEDが点滅すればOK
$ west flash
-- west flash: rebuilding
[0/16] Performing build step for 'tfm'
ninja: no work to do.
[2/3] Performing install step for 'tfm'
-- Install configuration: "MinSizeRel"
[3/3] Completed 'tfm'
-- west flash: using runner nrfjprog
Using board 1050088039
-- runners.nrfjprog: Flashing file: /home/hiroki/workspace/nrf-connect-sdk-tutorial/app/build/zephyr/merged.hex
[ #################### ]   1.911s | Erase file - Done erasing                                                          
[ #################### ]   0.406s | Program file - Done programming                                                    
[ #################### ]   0.303s | Verify file - Done verifying                                                       
Applying pin reset.
-- runners.nrfjprog: Board with serial number 1050088039 flashed successfully.
```
