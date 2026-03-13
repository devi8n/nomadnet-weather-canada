# Scraping/mirroring weather.gc.ca Pages over NomadNet

## Background

The Government of Canada has decided to shut down the weather broadcase service on AM radio and replace it with an app.
This is misguided because those most vulnerable to adverse weather conditions are least likely to have reliable access to the internet.


## Goals

The goal of this repo is to periodically scrape relevant pages from weather.gc.ca and display them on a NomadNet server.


## Basics

Pushing alerts probably wont work via Nomadnet, although it could be done with some kind of registration scheme where you subscribe to events and it pushes them out when they are detected. This may be possible in the future, but it may be better done over messaging/broadcast to some kind of group.

__This service is new and will be unreliable__ so don't rely on this to save your life. If you want a reliable service, this repo should contain all the pieces required to host this yourself on a node closer to you.


### NomadNet

A basic text-based protocol that runs on top of [Reticulum](https://unsigned.io).


### Reticulum

Reticulum is a protocol and routing technology that can operate over almost any medium - it can run over existing IP links, LoRa, packet radio, almost anything with a serial interface.
Encryption is mandatory, identity is public-key derived, routing is intelligent and flexible.


### weather.gc.ca

Provides weather information, along with the app WeatherCAN, which can push emergency alerts. There doesn't seem to be a public API to access the data, so it will probably require scraping.


## Hosting

A basic version might be a Docker container and/or instructions to run inside a VM (perhaps via Proxmox).


## Details

Python application with a sync loop every 10 minutes to scrape the relevant pages and convert them into .mu files and dump into the Nomadnet server directory.
Run `nomadnet` and `reticulum`.
Package as a container image (based on Alpine).
