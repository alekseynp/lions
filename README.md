# Lions Gate Bridge Community Project

The Lions Gate Bridge is a critical resource to the people of Vancouver. As citizens, we have the opportunity to gather and analyze data available online regarding the utilization of that resource.

## Readme Contents

- Project Goal
- Data
- Repository Structure
- Getting Started to Contribute
- Next Steps

## Project Goal

1. Confirm efficient resource management
2. Enable data services

### Confirm efficient resource management

Hypothesis:
- Lane management on the Lions Gate Bridge is not optimal
- A change in strategy could result in benefits for all
- We, as citizens, can discover this

Reasoning:
- We as a community are able to direct more raw analytical talent to this problem on a volunteer basis than the Ministry of Transportation can.

- In 2014 I requested data regarding the bridge and received the response below; we assert the response is intolerable for an important resource like the Lion's gate bridge, that the data must be retained and widely available.

> As for the data for Lion’s Gate Bridge, the ministry [of Transportation] does not retain the data. The data is collected by traffic counters and is translated to an image from the local infrastructure and transferred to the public website, however, the data that drives the map is not intentionally captured and is therefore, unfortunately, not available.

### Enable data services

Hypothesis:
- There exist opportunities for mobile and/or web applications based on the bridge and its data

Possible examples:
- Delay forecasts, both short term and long term
- Delay alerts

## Data

The data is being harvested over the internet from a number of places.

Data Summary

| Dataset | CSV Download Link | Definition | Frequency |
| ------- | ----------------- | ---------- | --------- |
| Map     | [map.csv](https://s3-us-west-2.amazonaws.com/lionsgatebridge/map.csv) | Lane directions, Segment congstions from ATIS | 1 minute |
| Sign    | [sign.csv](https://s3-us-west-2.amazonaws.com/lionsgatebridge/sign.csv) | Delay from Taylor Way to downtowm from Highway 1 ATIS sign | 1 minute |
| Google Northbound | [google_northbound.csv](https://s3-us-west-2.amazonaws.com/lionsgatebridge/google_northbound.csv) | Duration in traffic estimate from Google Northbound | 5 minutes |
| Google Southbound | [google_southbound.csv](https://s3-us-west-2.amazonaws.com/lionsgatebridge/google_southbound.csv) | Duration in traffic estimate from Google Southbound | 5 minutes |
| Traffic Cameras | Available on Request | Six traffic cameras | 1-5 minutes |
| Mapquest Traffic | Not Yet Available | Color-coded traffic estimates by segment from Mapquest | 5 minutes |
| Ferry Arrivals | Not Yet Available | Arrival times of ferries at Horseshoe Bay | 5 minutes |

An example of all of the current data presented for a single day:
![Mapquest Traffic Example](http://alekseymisc.s3.amazonaws.com/plot-2016-09-22.png)

### Map - Lanes Configuration and Congestion

This map, hotlinked live below, is available here on the [Lions Gate Bridge Advanced Traveller Information System](http://www.th.gov.bc.ca/ATIS/lgcws/) website.

![Lions Gate Map](http://www.th.gov.bc.ca/bchighwaycam/getFile.aspx?file=/ATIS/lgcws/images/Lions_gate/queue_map.gif)

The map includes:
- Current lane configuration
- Congestion estimates for 8 road segments

This map is being collected by a script once a minute, though it is mostly updated less frequently.

### Sign - Estimated Delay

The sign, hotlinked live below, is available here on the [Lions Gate Bridge Advanced Traveller Information System](http://www.th.gov.bc.ca/ATIS/lgcws/) website.

![Lions Gate Sign](http://www.th.gov.bc.ca/bchighwaycam/getFile.aspx?file=/ATIS/lgcws/images/Lions_gate/atis_delay.gif)

The sign is a simple estimate of the delay from Taylor Way to downtown Vancouver via the bridge.

This sign is being collected by a script once a minute, though it is mostly updated less frequently.

This data is available. See above for link.

### Google Driving Duration

Driving duration from the Taylor Way ramp to the intersection of West Georgia and Denman is being collected every minute.

This data is available. See above for link.

### Traffic Cameras

There are six traffic cameras relevant to the bridge. Hotlinked and live below. The cameras are being collected once a minute if they have been udpated which tends to occur once every 1-5 minutes.

It's not yet clear what will be done with this data, but it is a large data set available on request.

#### Camera 21
![Camera 21](http://images.drivebc.ca/bchighwaycam/pub/cameras/21.jpg)
[Link](http://www.th.gov.bc.ca/ATIS/lgcws/cctv1.html)

#### Camera 22
![Camera 22](http://images.drivebc.ca/bchighwaycam/pub/cameras/22.jpg)
[Link](http://www.th.gov.bc.ca/ATIS/lgcws/cctv2.html)

#### Camera 18
![Camera 18](http://images.drivebc.ca/bchighwaycam/pub/cameras/18.jpg)
[Link](http://www.th.gov.bc.ca/ATIS/lgcws/cctv4.html)

#### Camera 20
![Camera 20](http://images.drivebc.ca/bchighwaycam/pub/cameras/20.jpg)
[Link](http://www.th.gov.bc.ca/ATIS/lgcws/cctv6.html)

#### Camera 17
![Camera 17](http://images.drivebc.ca/bchighwaycam/pub/cameras/17.jpg)
[Link](http://www.th.gov.bc.ca/ATIS/lgcws/cctv27.html)

#### Camera 19
![Camera 19](http://images.drivebc.ca/bchighwaycam/pub/cameras/19.jpg)
[Link](http://www.th.gov.bc.ca/ATIS/lgcws/cctv50.html)

### Mapquest Traffic

A mapquest traffic map API call yields an estimate of current traffic on road segments around the bridge. A static example is below.

![Mapquest Traffic Example](http://alekseymisc.s3.amazonaws.com/20160828221057.png)

The data is being collected every 5 minutes to stay within the API rate limit.

The data is not yet processed and available for download.

### Ferry Data

Ferries arrive at Horseshoe Bay and create surges of demand for the Lions Gate Bridge. This is therefore potentially relevant data.

This page contains ferry arrival information for the current day: [Actual Departures](http://orca.bcferries.com:8080/cc/marqui/actualDepartures.asp) and is available normally [here](http://www.bcferries.com/current_conditions/actualDepartures.html).

This page is being collected once every 5 minutes.

The data is not yet processed and available for download.

## Repository Structure

This will develop with time. For now it's just files in the root.

## Getting Started to Contribute

Start a branch. Make pull requests.

The only thing not in the repo is the actual data. See above for links to download the CSV files.

Even if you aren't going to run the ipynb files, you can open them in GitHub and it renders the output for you to see.

Jupyter (IPython) Notebooks are currently the preferred tool for analysis, but definitely not a requirement. You might want to administer your own notebook server (I do). You might find it way easier to use the [Azure Notebooks Service](https://notebooks.azure.com/). I am using Python 3.

Feel free to start something with your own tool and add the associated scripts/whatever to the repo.

## Next Steps

Greater data availability.

Big juicy problems:
- Turn the camera images into estimates of current congestion and cross-validate with other source
- Identify an API that we can harvest better delay estimates from
- Simulation of the queuing/flow system
