# Configuration - settings.yaml

## Settings
This is where the global settings such as global variables, translations, excluded entities etc. are configured
To all parts new items can be added.

:warning: <sub>After making changes in settings.yaml you'll need to restart HomeAssistant</sub>

### Theme and path

| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `theme`         | string    | Required          | Name of the theme to use  |
| `dashboardPath` | string    | Required          | URL/Path to this dashboard, same as the name in `configuration.yaml` below `lovelace:` -> `dashboards:`  |

#### Example

```yaml
settings: 
  theme: "Aleborg Material"
  dashboardPath: "lovelace-aleborg"
```

### Header
This is used for the home/intro page, if you don't use the included `views/home.yaml` then this section can be removed.

| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `showTemperatureSensors` | boolean | Required   | Name of the theme to use  |
| `showHumiditySensors`    | boolean | Required   | Name of the theme to use  |
| `showMotionSensors`      | boolean | Required   | Name of the theme to use  |
| `showPrecenceSensors`    | boolean | Required   | Name of the theme to use  |
| `showIlluminanceSensors` | boolean | Required   | Name of the theme to use  |

#### Example

```yaml
settings: 
  ...
  header: 
      showTemperatureSensors: true
      showHumiditySensors: true
      showMotionSensors: false
      showPrecenceSensors: true
      showIlluminanceSensors: true
```

### Tabs
Here you can choose what tabs that should be visible and what icons the tabs should have.

| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `showLights`    | boolean   | Required          | Show or hide the lights tab  |
| `lightsIcon`    | string    | Required          | What icon to use for the lights tab  |
| `showMedia`     | boolean   | Required          | Show or hide the media tab  |
| `mediaIcon`     | string    | Required          | What icon to use for the media tab  |
| `showCalendar`  | boolean   | Required          | Show or hide the calendar tab  |
| `calendarIcon`  | string    | Required          | What icon to use for the calendar tab  |
| `showPower`     | boolean   | Required          | Show or hide the power usage tab  |
| `powerIcon`     | string    | Required          | What icon to use for the power usage tab  |

#### Example

```yaml
settings: 
  ...
  tabs:
    showLights: true
    lightsIcon: mdi:lightbulb-on-10
    showMedia: true
    mediaIcon: mdi:music
    showCalendar: true
    calendarIcon: mdi:calendar
    showPower: true
    powerIcon: fapro:usage
```

### Exclude entities
Here you can exclude entities, states and hidden entities that you don't want to be shown in the rooms/pages.\
You can do this for lights, media, scenes, the page header and for the power usage.\
You can read more about the filters here: **[auto-entities](https://github.com/thomasloven/lovelace-auto-entities)** by [@thomasloven](https://github.com/thomasloven/)

| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `entities`      | list      | Optional          | Entities  |
| `state`         | list      | Required          | Name of the theme to use  |
| `hidden_by`     | list      | Optional          | Name of the theme to use  |

#### Example

```yaml
settings: 
  ...
  excludeEntities: 
      lights: 
        entities: 
          - "switch.sp001_switch_power_monitor_belysning_koket"
          - "switch.wifi_plug_4_socket_1"
        state: 
          - "unavailable"
          - "unknown"     
        hidden_by: 
          - "user"
          - "integration"

      media:
        entities:
          - "media_player.sonos*" 
        state:
          - "unknown"
        hidden_by: 
          - "user"
          - "integration"

      page_header:
        state:
          - "unavailable"
          - "unknown"
        hidden_by: 
          - "user"
          - "integration"

      power_usage:
        state:
          - "unavailable"
          - "unknown"
        hidden_by: 
          - "user"
          - "integration"
      scenes:
        state:
          - "unavailable"
          - "unknown"
        hidden_by: 
          - "user"
          - "integration"
```

### Translations

You can easily add translations if you need it somewhere. The page need to start with `# lovelace_gen`.
The translations can be referenced with this code: `{{_global.tablet.settings.translations.power.powerConsumptionNow}}`

:warning: <sub>Removing any of the `powerConsumption` will also remove those gauges from the pages.\
In other words, if we remove i.e. `powerConsumptionYear` from translations, will cause all gauges with power consumption for the past year to be removed from all pages. </sub>

#### Example

```yaml
settings: 
  ...
  translations: 
    "OFF": "Off"
    power:
      powerConsumptionNow: "Current consumption"
      powerConsumptionToday: "Consumption today"
      powerConsumptionWeek: "Consumption past week"
      powerConsumptionMonth: "Consumption past month"
      powerConsumptionYear: "Consumption past year"
    home:
      apexCardElectricityPrices: "kWh Price"
      apexCardRightNow: "Now"
```

### Power consumption segments
The power consumption is shown in W and kWh, depending on your consumption you might want to change this so that the gauges don't end up on max or minimum with the needle. The segments currently exists in the segments from 0 to 10, 20, 30, 40, 50, 60, 70, 80, 90 and 100  

| Name            | Type      | Optional/Required | Measured in | Description            |
|:----------------|:---------:|:-----------------:|:-----------:|:-----------------------|
| `maxSegmentCurrent` | int   | Required          | W           | Current consumption |
| `maxSegmentDaily`   | int   | Required          | kWh         | Consumption today  |
| `maxSegmentWeekly`  | int   | Required          | kWh         | Consumption past week  |
| `maxSegmentMonthly` | int   | Required          | kWh         | Consumption past month  |
| `maxSegmentYearly`  | int   | Required          | kWh         | Consumption past year |

#### Example

```yaml
settings: 
  ...
  powerConsumptions:
    maxSegmentCurrent: 100
    maxSegmentDaily: 40
    maxSegmentWeekly: 20
    maxSegmentMonthly: 20
    maxSegmentYearly: 60
```

## Rooms and pages
This is where you configure the rooms

#### Shortcuts (below the clock in the sidebar)

<sub>:warning: Shortcuts will only display the icon</sub>

| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `title`         | string    | Required          | The name of the room/page, displayed in the sidebar and in the top of the page. |
| `url`           | string    | Required          | URL/Path in the browser for the page, should only be one word, i.e. `myroom`, can also contain hypens `my-room` |
| `icon`          | string    | Required          | The icon to use, i.e. `mdi:home` |
| `isShortcut`    | boolean   | Required          | Set this to `true` | 
| `file`          | string    | Optional          | Use _file_ to point the page to a custom file that exists in the folder _[views](../views/readme.md)_ |
| `sortOrder`     | int       | Required          | Specifies the order of the room in the menu | 

##### Example
```yaml
rooms:
  ...
  - title: "Hem"
    url: "home"
    file: "home.yaml"
    icon: "mdi:home"
    isShortcut: true
    sortOrder: 0
```

#### Floors / Subjects in the menu
| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `title`         | string    | Required          | The title of the floor |
| `sortOrder`     | int       | Required          | Specifies the order of the room in the menu | 

##### Example
```yaml
rooms:
  ...
  - title: "Upper floor"
    sortOrder: 3
```

#### Rooms


| Name            | Type      | Optional/Required | Description            |
|:----------------|:---------:|:-----------------:|:-----------------------|
| `title`         | string    | Required          | The name of the room/page, displayed in the sidebar and in the top of the page. <sub>:warning: Needs to be exactly the same as the area name!</sub> |
| `areaId`        | string    | Required          | ID of the area. <sub>:warning: Needs to be exactly the same as the area-id!</sub> |
| `icon`          | string    | Required          | The icon to use, i.e. `mdi:home` |
| `sortOrder`     | int       | Required          | Specifies the order of the room in the menu | 

##### Example
```yaml
rooms:
  ...
  - title: "Entrance" 
    areaId: "entrance"
    icon: "mdi:door-open"
    sortOrder: 9
```

## Full example
[Can be found here.](settings.yaml)