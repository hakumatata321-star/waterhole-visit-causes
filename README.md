# Waterhole Visit Causes

## Overview

This dataset contains 1,000 synthetic dry seasons at a waterhole. In each, 10 to 19 collared herds of zebra, buffalo, blue wildebeest and greater kudu come to drink over 45 days. Every arrival is recorded from GPS collar fixes, together with the daily maximum temperature. The reason for each arrival, whether the herd's own routine, thirst after heat, or following another herd to the water, is recorded in a separate table and is the quantity of interest.

Nothing here is observed in the field. Every season, herd, arrival and identifier is produced by a generator whose draws are HMAC-SHA256 keyed to a withheld 256-bit secret, so no part of the release can be regenerated or matched against any public archive.

## Release At A Glance

- 1,000 seasons, 14,553 herds, 435,418 recorded visits.
- 45 days per season, with a daily maximum temperature for each day.
- Four species, one collar per herd; each herd's arrival is one visit.
- Arrivals timed by 10-minute GPS fixes, of which some are lost, at most three in a row.
- A season is the independent unit: its herds and visits belong to it alone.

## How The Data Was Generated

Each herd has a drinking rhythm of its own, a rate at which it loses water in the heat, a level of dehydration at which it will come to drink regardless of its rhythm, and a set of other herds it associates with. None of these is recorded. Each day, a herd whose water balance has fallen past its limit comes to drink; otherwise a herd whose rhythm is due comes at around its usual hour; and a herd that associates with an arriving herd may come in behind it. Drinking restores the herd's water balance.

The settings follow published dry-season field studies: how often these species drink, when in the day they arrive, how heat raises drinking, how herds arrive as units, and how often GPS fixes are lost. Three settings have no published figure behind them and are ours: how often greater kudu drink, how much more often herds drink per degree of heat, and how long after its leader a following herd arrives.

## Files

- `seasons.csv`: one row per season, with the number of herds and days.
- `herds.csv`: one row per herd, with its season and species.
- `temperature.csv`: one row per season and day, with the daily maximum temperature in degrees Celsius.
- `visits.csv`: one row per recorded visit, with its season, herd and arrival time in minutes from the start of the season.
- `causes.csv`: one row per visit, with its cause: `routine`, `thirst`, or `follow:<visit_id>` naming the visit it came in behind.
- `LICENSE`: CC BY 4.0.
- `DATASET_DESCRIPTION.md`: this description, shipped inside the archive so the card and the data cannot drift apart.
- `PACKAGE_MANIFEST.sha256`: a SHA-256 for every other file, so the archive can be verified after download.

## Intended Use And Limitations

The dataset is intended for work on attributing events to their causes when the causes are internal states, individual rhythms and social ties that are never observed. It is fully synthetic. It simplifies real waterhole behaviour, leaving out predators, other water sources and individual animals within a herd, and results on it say nothing about any real population.

## Licence

CC BY 4.0. The dataset is synthetic and contains no personal data and no third-party material.

## Data access

The data files are distributed with the challenge that uses them and are not stored here. The generator is keyed to a withheld secret and is not published, so the release cannot be regenerated or matched against any external source.
