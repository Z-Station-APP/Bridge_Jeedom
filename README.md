# Z-Station Bridge for Jeedom

The **Z-Station Bridge for Jeedom** allows the Z-Station mobile application to communicate directly with Jeedom through a dedicated REST API.

This plugin acts as a **bridge** between Jeedom and the Z-Station ecosystem:

- It exposes Jeedom devices in a structured and optimized JSON format  
- It allows the mobile app to refresh device states  
- It supports execution of actions (ON/OFF, dimming, temperature setpoints, etc.)  
- It exposes Jeedom objects (rooms) for device organization  

The Z-Station app can interact with Jeedom **natively**, without any additional configuration.

---

## Features

- Exposes Jeedom devices and their state via a lightweight REST API  
- Real-time device refresh and state retrieval  
- Ability to execute Jeedom actions from the Z-Station app  
- Returns Jeedom objects (rooms) as Z-Station “zones”  
- No dependencies or external services required  
- Works on Jeedom v4 and above  

---

## REST API Endpoints

The plugin provides the following API routes for the Z-Station application:

### `GET /api/zstation/getdevices`
Returns:
- all Jeedom devices
- states  
- attributes  
- associated room (“zone”)  

### `GET /api/zstation/refresh_devices`
Returns updated device states only.

### `POST /api/zstation/execute_action`
Executes an action on a Jeedom device.

Example body:
```json
{
  "entity_id": "light.23",
  "service": "turn_on",
  "data": {}
}
```

### `GET /api/zstation/getzone`
Returns Jeedom objects (rooms) as Z-Station zones.

---

## Installation

1. Copy the plugin folder into Jeedom:

```
/var/www/html/plugins/zstation/
```

Required structure:

```
zstation/
 ├── plugin_info/
 │     └── info.xml
 ├── core/
 │     ├── class/
 │     │     └── zstation.class.php
 │     └── api/
 │           ├── getdevices.php
 │           ├── refresh_devices.php
 │           ├── execute_action.php
 │           └── getzone.php
 ├── desktop/
 │     └── php/
 │           └── zstation.php
 ├── resources/ (optional)
 └── README.md
```

2. In Jeedom, go to:

**Plugins → Plugin Management → Add Plugin → Manual installation**

3. Install and activate the plugin.

No configuration is required after installation.

---

## Testing the API

You can test an endpoint directly in your browser or an HTTP tool:

```
http://YOUR_JEEDOM_IP/plugins/zstation/core/api/getdevices.php
```

If installed correctly, a JSON response will be returned.

---

## Plugin Structure

```
plugins/
 └── zstation/
       ├── plugin_info/info.xml
       ├── core/class/zstation.class.php
       ├── core/api/getdevices.php
       ├── core/api/refresh_devices.php
       ├── core/api/execute_action.php
       ├── core/api/getzone.php
       ├── desktop/php/zstation.php
       └── README.md
```

---

## Compatibility

- Jeedom v4.x and above  
- Works on: Raspberry Pi, Debian, Ubuntu, Docker, VM, NAS  
- Fully compatible with the Z-Station mobile app (Android / iOS)

---

## License

MIT License

---

## Author

Xeos – Z-Station App

