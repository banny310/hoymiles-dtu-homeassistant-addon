
# Hoymiles DTU Solar Data Gateway Add-on

An application to read Hoymiles Gateway Solar Data using direct communication with Hoymiles DTU

I have done this addon to integrate my solar system data with our [Home Assistant](https://www.home-assistant.io/) instance.

## Pros:
- data update interval 1 minute instead of default 15 minutes on global.hoymiles.com
- detailed info from separate inverters (ex.: reactive power, power factor) and each panel individually

## Cons:
- tested only on DTU-Pro (see notice below)

Screen from home assistant
<img src="https://github.com/banny310/hoymiles-dtu-homeassistant-addon/raw/master/img/dtu_ha.png" alt="" width="800" />

## How it works

Add-on sets connection with Hoymiles DTU unit and starts listening for incoming data.
When new data is received add-on will transform it and push to mqtt broker.

On start add-on changes server send time configuration on dtu from 15 minutes (dtu default) to 1 minute.
After that data is refreshed every minute in Home Assistant and native Hoymiles dashboard also.

## Dependencies

- Hoymiles DTU (currently tested only on DTU-Pro)
- Home Assistant with Mosquitto Add-on installed (MQTT)


### Notice:
> DTU must be connected to your local network by WIFI (not by LAN).\
> Only on WIFI interface DTU can be accessed on port 10081

## Installation

1. Copy this repository url https://github.com/banny310/hoymiles-dtu-homeassistant-addon
2. Add as new repository in Home Assistant add-on store
3. Install add-on
4. Set DTU ip address and port in config tab
```yaml
dtu:
    host: 192.168.88.129
    port: 10081
```
5. Start add-on

## Configuration

An add-on full, default configuration is showed bellow\
You may override that in home assistant yaml addon config (make sure you match structure)
```
dtu = {
    host = 192.168.1.1
    port = 10081
    watchdog_timeout = 300              # Restart connection to DTU when nothing is received from DTU in period of time (seconds)
                                        # Useable in passive mode because sometimes communication stalls
}
mqtt = {
    host = 192.168.1.2
    port = 1883
    username = xxx
    password = xxx-password
}
app = {
    store_messages_in_excel = false     # used to save received messages in excel format for debug purposes
    mode = passive                      # add-on work strategy, values: [active, passive]
                                        #   active    - addon continously pool DTU for statistics. 
                                        #               Default every 1 minute
                                        #   passive   - addon changes time interval with DTU send statistics to 
                                                        hoymiles.com and starts passive listenting to outgoing communication               
    mode_active = {
        pull_interval = 60              # time in seconds between each metrics request from DTU
    }
    mode_passive = {
        set_server_send_time = true     # change DTU configuration of report statistics time interval
        server_send_time = 1            # report statistics to hoymiles.com time interval in minutes (dtu default: 15 minutes)
    }
}
```

Example override of watchdog_timeout in yaml:

```yaml
dtu:
    host: 192.168.88.129
    port: 10081
    watchdog_timeout: 600
```

## Notice and Warning!

Currently, tested only with DTU-Pro:
- hw: H09.01.02 
- sw: V00.02.08, V00.02.10, V00.02.15 (V00.02.0F)

If you have a version other than those listed above, run it at your own risk!

#### Licence

> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
