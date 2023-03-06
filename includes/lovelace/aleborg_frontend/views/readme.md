# Folder: _views_
In this folder you should add additional customized pages.

### [page.yaml](page.yaml)
This file should not be removed, it contains the code for all auto-generated pages.

### [home.yaml](home.yaml)
This file displays the home page.

**_Todo_**
- [ ] _Make home.yaml general, for the moment it needs to be customized._

### [lights.yaml](lights.yaml)
This file displays a list of ALL lights.

### [zigbeemap.yaml](zigbeemap.yaml)
Displays a map of the zigbee network, can be turned off in [settings.yaml](../settings.yaml)

## How-To
When creating a new file add this code:

```yaml
theme: {{ _global.tablet.settings.theme}}
title: {{title}}
path: {{url}}
icon: {{icon}}
type: custom:ha-dashboard
usePanel: true
style: !include ../templates/sidebar/styles/styles.yaml
sidebar: 
  stickyCards:
    - type: custom:digital-clock
      locale: sv
  cards: !include ../templates/sidebar/menu.yaml
cards:
  # Add your cards here
```
You will also need to add the file in the section `room:` in [_settings.yaml_](../settings.md)
