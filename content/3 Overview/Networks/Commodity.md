---
title: Commodity
description: 
permalink: 
aliases: 
draft: false
date: 2024-09-27
tags:
  - Commodity
  - Overview
  - ToDo
---
[[./Commodity Networks|previous]] [[./Network Ontology|next]] 
# Commodity

The commodity of a network is what is being transported by it.
The items in the commodity are abbreviated to facilitate reading and save database space.

It has one, two or three components:

| Order | Name       | Description |
| ----: | ---------- | ----------- |
|     1 | Subnetwork | Meaningful subdivision of the network, for example an abbreviation high voltage DC (elec), high voltage AC, low voltage, service (water), transport, distribution, intake, high pressure (gas), low pressure, UTP (telco), coax, middle band, red light, green light. |
|     2 | Function   | A component of the subnetwork, e.g. 150kV, 400V, water quality. |
|     3 | Details    | Phase information, CH4 (high caloric), H2, channel info. |

In NetCon, the commodity is specified during the extraction.
The different components are separated with a ':' symbol.

If only a two components is specified, then these are interpreted as "Subnetwork::Details".

It is possible to specify a `secondary commodity` by typing a a '|' and then specifying the secondary commodity.
Typical secondary commodities are 'CP' for cathodic protection or 'PL' for public lighting. 

In the following table some examples are provided per network type:

| Network | Example              | Meaning                                                                                                            |
| ------: | -------------------- | ------------------------------------------------------------------------------------------------------------------ |
|       E |                      | **Electric network**                                                                                               |
|       E | UHV                  | ultra high voltage, default is AC                                                                                  |
|       E | UHV:1100000          | ultra high voltage, 1100kV                                                                                         |
|       E | UHVDC:800000         | ultra high voltage DC (Used in China)                                                                              |
|       E | EHV                  | extra high voltage                                                                                                 |
|       E | EHV:400000           | extra high voltage, 400kV (used in the UK and Scandinavia)                                                         |
|       E | EHVDC:400000         | extra high voltage DC, 400kV (used in the North Sea)                                                               |
|       E | EHV:380000           | extra high voltage (used in Europe)                                                                                |
|       E | EHV:380000:ABC       | extra high voltage, 380kV, phases ABC, earth shield is assumed for underground cables                              |
|       E | EHV:275000           | extra high voltage, 275kV (used in the UK and Scandinavia)                                                         |
|       E | HV                   | high voltage                                                                                                       |
|       E | HV:220000            | high voltage, 220kV phases ABC are assumed                                                                         |
|       E | HV::A                | high voltage, phase A                                                                                              |
|       E | HV::B                | high voltage, phase B                                                                                              |
|       E | HV::C                | high voltage, phase C                                                                                              |
|       E | HV::U                | high voltage, single (unknown) phase                                                                               |
|       E | HV::E                | high voltage, earth wire or shield; for normal cables assumed to be there                                          |
|       E | HV::ABC              | high voltage, phases ABC, earth shield is assumed                                                                  |
|       E | HV::ABCN             | high voltage, phases ABC and neutral, earth shield is assumed                                                      |
|       E | HV:150000:ABC        | high voltage, 150kV phases ABC                                                                                     |
|       E | HV:110000            | high voltage, 110kV phases ABC are assumed                                                                         |
|       E | HV:50000:ABC         | high voltage, 50kV, phases ABC, earth shield is assumed                                                            |
|       E | MV                   | medium voltage, same high voltage examples above                                                                   |
|       E | MV:20000             | medium voltage, 20kV                                                                                               |
|       E | MV:10000             | medium voltage, 20kV                                                                                               |
|       E | MV:8000,ABCN         | medium voltage, 8kV, phases ABC and neutral, earth shield is assumed                                               |
|       E | MV:3000,ABC          | medium voltage, 8kV, phases ABC and no neutral, earth shield is assumed                                            |
|       E | LV                   | low voltage                                                                                                        |
|       E | LV:U                 | low voltage, single (unknown) phase                                                                                |
|       E | LV:ABC               | low voltage, phase ABC                                                                                             |
|       E | LV:ABCN              | low voltage, phase ABC                                                                                             |
|       E | LV:400:ABCN          | low voltage, 400 AC (Used in European network)                                                                     |
|       E | LV:230:A             | low voltage, phase A, 230 AC                                                                                       |
|       E | LV:380:ABC;LV:115:UN | low voltage, used in Japan East, 50Hz. 3 phases of 200 volt and single phase 115.                                  |
|       E | LV:380:ABC;LV:115:UN | low voltage, used in Japan West 60Hz. 3 phases of 200 volt and single phase 115.                                   |
|       E | LV:400:ABC;LV:121:UN | low voltage, used in Japan West 60Hz. 3 phases of 210 volt and single phase 121.                                   |
|       E | PL                   | public lighting only                                                                                               |
|       E | LV;PL                | lowvoltage and public lighting as secondary commodity                                                              |
|       E | LV::ABCN;PL          | lowvoltage with three phase and neutral and public lighting as secondary commodity, used in so called combi-cables |
|       G |                      | **Gas network**                                                                                                    |
|       G | HP                   | high pressure gas                                                                                                  |
|       G | HP:8                 | high pressure gas, 8 bar                                                                                           |
|       G | HP:8\|CP             | high pressure gas, 8 bar and cathodic protection as secondary commodity                                            |
|       G | HP:4                 | high pressure gas, 4 bar                                                                                           |
|       G | HP:4:LC              | high pressure gas, 4 bar, Low Caloric                                                                              |
|       G | HP:1:HC              | high pressure gas, 1 bar, High Caloric                                                                             |
|       G | LP                   | low pressure gas                                                                                                   |
|       G | LP:1                 | low pressure gas                                                                                                   |
|       G | LP:0.4               | low pressure gas, 0.4 bar                                                                                          |
|       G | LP:0.1:H2            | low pressure gas, 0.1 bar, hydrogen                                                                                |
|       G | CP                   | cathodic protection                                                                                                |
|       H |                      | **Heath network**                                                                                                  |
|       H | HT                   | High grade temperature, > 70ᵒC at end consumers                                                                    |
|       H | MT                   | Medium grade temperature, 55ᵒ - 70ᵒC at end consumers                                                              |
|       H | LT                   | Low grade temperature, < 55ᵒC at end consumers                                                                     |
|       W |                      | **Water network**                                                                                                  |
|       T |                      | **Telecom network**                                                                                                |

#ToDo Write more examples.
Especially some with CP and PL.

A special case is a steel pipe transporting gas or water, that is cathodic-protected as well.
In this case, it transports gas or water on the inside, and it has a small electric current on the outside.
#ToDo

Sometimes the commodity is not registered with an asset, but it needs to be derived as a [[./Derived Commodity|Derived Commodity]].

