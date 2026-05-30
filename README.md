# Cradlewise Smart Crib for Home Assistant

Home Assistant integration for the [Cradlewise Smart Crib](https://www.cradlewise.com/) using the unofficial API.

This integration queries the Cradlewise cloud REST API Gateway to fetch cradle state and sleep analytics via a coordinator polling mechanism. Real-time local controls and push events can be set up separately using the local MQTT bridge.

> **Note:** This uses an unofficial API. Cradlewise may change or restrict access at any time.

## Exposed Entities

### Core Sensors
- **Sleep Stage**: Current granular sleep stage (Deep Sleep, Light Sleep, Quiet Awake, etc.)
- **Sleep Phase**: Current coarse sleep phase (Away, Awake, Stirring, Sleep, Unknown)
- **Bounce Amplitude**: Current rocking motor amplitude (discrete level)
- **Music Volume**: Current white noise/music volume level
- **Music Track**: Current white noise/music track name
- **Temperature**: Current room temperature in Celsius
- **Day Start Time**: Configured rising boundary starting time (Diagnostic)
- **Firmware Version**: System software version (Diagnostic, disabled by default)

### Analytics Sensors (Sleep & Aggregates)
- **Today's Soothe Count**: Number of times the crib has initiated soothing today
- **Today's Sleep Saved**: Estimated sleep duration saved by soothing today
- **Today's Nap Count**: Total number of naps recorded today
- **Today's Rise Time**: Recorded morning rise time today
- **Today's Bedtime**: Recorded evening bedtime today
- **Today's Time in Bed**: Recorded total duration spent in bed today
- **Today's Longest Stretch**: Duration of the longest continuous sleep stretch today
- **Today's Awake in Bed**: Total duration spent awake while in bed today
- **Weekly Average Sleep**: Daily average sleep duration over the past week
- **Weekly Average Day Sleep**: Daily average day sleep duration over the past week
- **Weekly Average Night Sleep**: Daily average night sleep duration over the past week
- **Weekly Average Nap Duration**: Average duration of individual naps over the past week
- **Weekly Average Naps per Day**: Average number of naps per day over the past week
- **Weekly Average Rise Time**: Average rising time over the past week
- **Weekly Average Bedtime**: Average bedtime over the past week
- **Weekly Average Longest Stretch**: Average longest sleep stretch over the past week
- **Baby Age**: Baby's age description
- **Last Nap Start**: Timestamp when the most recent nap began
- **Last Nap End**: Timestamp when the most recent nap ended
- **Last Event**: Text description/message of the last recorded status change (with timestamp attribute)

### Binary Sensors
- **Connectivity**: Online connection status of the crib to the cloud
- **Occupancy**: Baby present in the crib (Occupancy class)
- **Crib Helping**: Binary indicator showing if the crib is actively soothing (bouncing or running recipes)
- **Bouncing**: Rocking motor state
- **Music Playing**: White noise state
- **Light On**: Nightlight state
- **In Sleep Schedule**: Binary indicator showing if the crib is inside the configured sleep schedule
- **In Soothing Window**: Binary indicator showing if the crib is inside the soothing window
- **Rocking Not Effective**: Warning indicator indicating if rocking has been ineffective

## Installation

### Via HACS (Recommended)

1. Open **HACS** in your Home Assistant instance.
2. Click the three dots in the top-right corner and select **Custom repositories**.
3. Add the following repository URL:
   `https://github.com/grantland/ha-cradlewise`
4. Set the category to **Integration** and click **Add**.
5. Find the **Cradlewise Smart Crib** integration in HACS and click **Download**.

### Manually

Copy the `custom_components/cradlewise` directory to your Home Assistant `config/custom_components/` directory.

## Setup

1. Restart Home Assistant.
2. Go to **Settings → Devices & Services → Add Integration**.
3. Search for **Cradlewise**.
4. Enter your Cradlewise account email and password.
