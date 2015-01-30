# node-red-contrib-advanced-ping

A <a href="http://nodered.org" target="_new">Node-RED</a> node which takes input and pings a remote server.

This is a modification of the [node-red-node-ping](https://github.com/node-red/node-red-nodes/tree/master/io/ping) node. Difference is that this node **will perform a ping when it recieves input** where the node-red-node-ping node performs pings on a set interval. You may also programmatically pass ping settings to this node. For periodical checks, wire an inject node to this ping node.


## Install

Run the following command in the root directory of your Node-RED install

    npm install node-red-contrib-advanced-ping

## Usage

* Pings a machine and returns the trip time in ms. Ping time is returned in `msg.payload`. Returns boolean **false** if no response received within 5 seconds, or if the host is unresolveable.
* Will perform ping on **any** input.
* You may override the host set in the configuration by passing in a value in `msg.host`.
* For legacy reasons, the node will output the host as `msg.topic` (the original [node-red-node-ping](https://github.com/node-red/node-red-nodes/tree/master/io/ping) does it this way).
* Any incomming data will be passed on to the output.
  * Incoming `msg.payload` data will be outputted as `msg._payload` (as the new `msg.payload` will contain the result of the ping).
  * Incoming `msg.topic` data will be outputted as `msg._topic` (as the new `msg.topic` will contain the the host).

## Todo
Ability to set ping options in node configuration/by incomming message. Right now, these settings are hardcoded

* Linux: -n -w 5 -c 1
* Windows: -n 1 -w 5000
* Mac: -n -t 5 -c 1