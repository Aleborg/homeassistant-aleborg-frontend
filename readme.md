# Aleborg Frontend

This is a complete frontend for [HomeAssistant](https://home-assistant.io)

I've tried to make this frontend as automated as possible. Due to restrictions in the frontend, a lot of things needs to be configured in the file [/includes/lovelace/aleborg_frontend/settings.yaml](settings.md).

This frontend doesn't have support for all types of devices and entities due to the fact that I don't have all different devices, such as covers. [A list of my hardware can be found here](hardware.md).

There's still a lot to do in this frontend and my CSS skills sucks, so all help is welcome! 

:warning: All files and folders needs to be placed in the folder `config`

<a href="https://www.buymeacoffee.com/aleborg"><img src="https://img.buymeacoffee.com/button-api/?text=Buy me a coffee&emoji=&slug=aleborg&button_colour=5F7FFF&font_colour=ffffff&font_family=Cookie&outline_colour=000000&coffee_colour=FFDD00" /></a>

## Table of Content <!-- omit in toc -->
- [Aleborg Frontend](#aleborg-frontend)
  - [Requirements](#requirements)
    - [Frontend (HACS)](#frontend-hacs)
    - [Integrations (HACS)](#integrations-hacs)
  - [configuration.yaml](#configurationyaml)
    - [Lovelace configuration](#lovelace-configuration)
    - [Theme configuration](#theme-configuration)
  - [Resources](#resources)
  - [Settings](#settings)
    - [/includes/lovelace/aleborg\_frontend/settings.yaml](#includeslovelacealeborg_frontendsettingsyaml)
  - [Folders and descriptions of files](#folders-and-descriptions-of-files)
    - [/includes/lovelace/aleborg\_frontend/common](#includeslovelacealeborg_frontendcommon)
    - [/includes/lovelace/aleborg\_frontend/templates](#includeslovelacealeborg_frontendtemplates)
    - [/includes/lovelace/aleborg\_frontend/views](#includeslovelacealeborg_frontendviews)
  - [Screenshots](#screenshots)
    - [Home](#home)
    - [All lights](#all-lights)
    - [Lights in a room](#lights-in-a-room)
    - [Multimedia in a room](#multimedia-in-a-room)
    - [Calendar in a room](#calendar-in-a-room)
    - [Power usage in a room](#power-usage-in-a-room)

## Requirements

### Frontend (HACS)
* **[layout-card](https://github.com/thomasloven/lovelace-layout-card)** by [@thomasloven](https://github.com/thomasloven/)
* **[auto-entities](https://github.com/thomasloven/lovelace-auto-entities)** by [@thomasloven](https://github.com/thomasloven/)
* **[card-mod 3](https://github.com/thomasloven/lovelace-card-mod)** by [@thomasloven](https://github.com/thomasloven/)
* **[state-switch](https://github.com/thomasloven/lovelace-state-switch)** by [@thomasloven](https://github.com/thomasloven/)
* **[Button Card](https://github.com/custom-cards/button-card)** by [@RomRider](https://github.com/RomRider)
* **[ApexCharts Card](https://github.com/RomRider/apexcharts-card)** by [@RomRider](https://github.com/RomRider)
* **[Config Template Card Card](https://github.com/iantrich/config-template-card)** by [@iantrich](https://github.com/iantrich)
* **[Digital Clock](https://github.com/wassy92x/lovelace-digital-clock)** by [@wassy92x](https://github.com/wassy92x)
* **[HA Dashboard](https://github.com/wassy92x/lovelace-ha-dashboard)** by [@wassy92x](https://github.com/wassy92x)
* **[Vertical Stack In Card](https://github.com/ofekashery/vertical-stack-in-card)** by [@ofekashery](https://github.com/ofekashery)
* **[Mini Media Player](https://github.com/kalkih/mini-media-player)** by [@kalkih](https://github.com/kalkih)
* **[Sonos card for Home Assistant's Dashboard UI](https://github.com/johanfrick/custom-sonos-card)** by [@johanfrick](https://github.com/johanfrick)
* **[Mushroom](https://github.com/piitaya/lovelace-mushroom)** by [@piitaya](https://github.com/piitaya)
* **[Mushroom Themes](https://github.com/piitaya/lovelace-mushroom-themes)** by [@piitaya](https://github.com/piitaya)
* **[Kiosk Mode](https://github.com/NemesisRE/kiosk-mode)** by [@NemesisRE](https://github.com/NemesisRE)
* **[Home Assistant Swipe Navigation](https://github.com/zanna-37/hass-swipe-navigation)** by [@zanna-37](https://github.com/zanna-37)
* **[Tabbed Card](https://github.com/kinghat/tabbed-card)** by [@kinghat](https://github.com/kinghat)

### Integrations (HACS)
* **[lovelace_gen](https://github.com/thomasloven/hass-lovelace_gen)** by [@thomasloven](https://github.com/thomasloven/)
* **[fontawesome](https://github.com/thomasloven/hass-fontawesome)** by [@thomasloven](https://github.com/thomasloven/)
* **[Nord Pool integration for Home Assistant](https://github.com/custom-components/nordpool)** by [@custom-components](https://github.com/custom-components)
* **[Variable](https://github.com/snarky-snark/home-assistant-variables)** by [@snarky-snark](https://github.com/snarky-snark)



## configuration.yaml

### Lovelace configuration
Add to your `configuration.yaml` these lines:
```yaml
#########################################################
# Lovelace                                              #
#########################################################
lovelace_gen:
  tablet: !include includes/lovelace/aleborg_frontend/settings.yaml

lovelace:
  dashboards:
    lovelace-aleborg: # Needs to contain a hyphen (-)
      mode: yaml
      filename: includes/lovelace/aleborg_frontend/tablet.yaml # or the path to where you added the folder
      title: Aleborg Frontend
      icon: mdi:tools
      show_in_sidebar: true
      require_admin: false
```
### Theme configuration
Included is a custom theme, it's placed in the directory `config/themes`, if it don't exist create it and add the following to your `configuration.yaml`

```yaml
#########################################################
# Themes                                                #
#########################################################
frontend:
  themes: !include_dir_merge_named themes
```

## Resources
Add following resource in ***`Settings -> Dashboards`***, click on the three dots in the upper right corner and choose ***`Resources`***, click on ***`+ ADD RESOURCE`*** in the lower right corner.

```
URL: https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&family=Ubuntu:ital,wght@0,300;0,400;0,700;1,300;1,400;1,700&display=swap
Resource type: Stylesheet
```
## Settings

All configuration options for this frontend is defined here:

### [/includes/lovelace/aleborg_frontend/settings.yaml](settings.md)

## Folders and descriptions of files

### [/includes/lovelace/aleborg_frontend/common](/includes/lovelace/aleborg_frontend/common/readme.md)

### [/includes/lovelace/aleborg_frontend/templates](/includes/lovelace/aleborg_frontend/templates/readme.md)

### [/includes/lovelace/aleborg_frontend/views](/includes/lovelace/aleborg_frontend/views/readme.md)

## Screenshots
### Home
![Home](includes/lovelace/screenshots/home.png)
### All lights
![All lights](includes/lovelace/screenshots/all_lights.png)
### Lights in a room
![Lights in a room](includes/lovelace/screenshots/lights.png)
### Multimedia in a room
![Media](includes/lovelace/screenshots/media.png)
### Calendar in a room
![Calendar](includes/lovelace/screenshots/calendar.png)
### Power usage in a room
![Power Usage](includes/lovelace/screenshots/power_usage.png)