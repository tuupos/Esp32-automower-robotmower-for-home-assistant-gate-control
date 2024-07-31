# Esp32-automower-robotmower-for-home-assistant-gate-control
ESP32 electric automower-gate control with feedback and optional control from home assistant

Local electric gate-lock control at the gate where husqvarna automower passes through and sending info back to Home Assistant

Since we have a garden as in front-yard and back-yard devided by a hedge there was for me no alternative for the Husqvarna automower 415x to go from back (where the docking station is) to the front other then creating a gate. After some prototyping of gates I ended up with a swing gate. It had to be locked when no mower goes through because our dog will go trough it too and end up on the street which is, of course, dangerous as our dog doesnt follow the traffic rules.


**Beginning**

It al started with a zigbee relay switch and a normally-closed 12v electric bolt-lock. The zigbee relay switch I bought online and made in node-red for home-assistant a flow that when the mower left the dock ("leaving dock is on") for 120s then node-red send a signal to the switch trough zigbee to open the gate (it takes the mower just more then 120s to reach the gate from the docking station when leaving and following the guidewire). After it went trough the gate and started mowing "(leaving dock is off)" a node-red flow would send a zigbee command to close the gate and the gate would lock.


**Problems**

The only problem is that if for some reason the connection to the Husqvarna cloud-api is disconnected the gate would not open since there is nog leaving_dock command issued. Even so whem Home assistant would be down or issues with Zigbee2mqqt (not starting) or other software issues , the gate would not open. So I wanted a more independend control of the gate but stil get informed in home assistant and I should also be able to controle it trough home assistant if needed


**Solution**

ESP32 connected to a low_voltage (3.3v) trigger relay.



**_I am not a programmer, nor do I work in the IT business, I'm just a enthousiastic hobbiest and learn to alter code but I'm not good at writing code from scratch. Thanks to github and other resources (nowadays also AI) I can create what I need, Therefor doný shoot at my code. It can possibly be shorter or better but when it works, it works._**
