
# Hoymiles DTU Solar Data Gateway Add-on

An application to read Hoymiles Gateway Solar Data using direct communication with Hoymiles DTU

I have done this addon to integrate my solar system data with our [Home Assistant](https://www.home-assistant.io/) instance.

## Pros:
- data update interval 1 minute instead of default 15 minutes on global.hoymiles.com
- detailed info from separate inverters (ex.: reactive power, power factor) and each panel individually

Screen from home assistant
<img src="https://github.com/banny310/hoymiles-dtu-homeassistant-addon/raw/master/img/dtu_ha.png" alt="" width="800" />

## How it works

Add-on sets connection with Hoymiles DTU unit and starts listening for incoming data.
When new data is received add-on will transform it and push to mqtt broker.

On start add-on changes server send time configuration on dtu from 15 minutes (dtu default) to 1 minute.
After that data is refreshed every minute in Home Assistant and native Hoymiles dashboard also.

## Installation

1. Copy this repository url https://github.com/banny310/hoymiles-dtu-homeassistant-addon
2. Add as new repository in Home Assistant add-on store

## Notice and Warning!

Currently, tested only with DTU-Pro:
- hw: H09.01.02 
- sw: V00.02.08, V00.02.10

If you have a version other than those listed above, run it at your own risk!

#### Licence

> THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
