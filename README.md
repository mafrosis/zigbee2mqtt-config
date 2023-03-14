zigbee2mqtt-config
==========

Configuration for my zigbee2mqtt setup.


Zigbee Gateway
----------

HamGeek Zigbee controller based on CC2652P chipset. Connected via LAN to POW switch, the controller
UI can be found at http://zigstargw.eggs.

The vendor docs [can be found here](https://docs.google.com/document/d/1jTb5zv91QcaXOcuIfqH5Ss0eCGM6MlBZ/edit).  

The `zigbee2mqtt.yaml` config required is:
```
serial:
  port: tcp://zigstargw:6638
```


Troubleshooting
----------

### Debugging tools

In `zigbee2mqtt.yaml`:

```
advanced:
  log_level: debug
```

In `docker-compose.yml`:

```
- DEBUG=zigbee-herdsman*
```

### Migrating from another Zigbee network

`zigbee2mqtt` will always use the same default `panId` and `extendedPanId` unless you set it to
something else in the config file:

```
advanced:
  pan_id: GENERATE
  ext_pan_id: [0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07, 0x08]
  network_key: GENERATE
```
