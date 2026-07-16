# Interview notes

## 30-second summary

I analysed synthetic water-quality data from four tilapia tanks. I cleaned labels and duplicates, flagged impossible values, checked missing data and plotted the six signals over time. I then used a rolling z-score on daily ammonia to find a biofilter problem. I checked the other signals and saw that pH and dissolved oxygen moved in the opposite direction across all tanks, which suggested a real process event rather than one faulty sensor.

## Why did you use synthetic data?

It gave me known unusual events, so I could check whether my cleaning and analysis found the correct patterns. I would need operator and maintenance records to validate events in real data.

## Why did you leave the logger outage missing?

All six measurements were missing for two days. Interpolating such a long gap would invent data, so I kept the rows as missing and added a flag.

## Why did you use a rolling z-score?

It is simple to calculate and explain. It compares each daily value with the recent average and variation. I chose it because the aim was to build a clear baseline before trying more complex models.

## How did you separate a process event from a sensor fault?

A sensor fault appeared on one tank or one signal. During the biofilter event, ammonia increased while pH and DO decreased across all four tanks. The signals changed together in a way that made sense for the process.

## What would you improve next?

I would add real feeding and maintenance logs, test the alert on a longer time period, and compare the simple rule with one machine-learning method after establishing the baseline.

## Details worth remembering

- Four tanks × 90 days × 144 readings/day = 51,840 expected rows.
- The raw file had 25 extra duplicate rows.
- The two-day logger outage affected 288 rows.
- The detected event began on 25 April 2026.
- Ammonia and turbidity are strongly related because both rise after feeding.
