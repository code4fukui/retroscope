# Retroscope Sabae

> 日本語のREADMEはこちらです: [README.ja.md](README.ja.md)

[
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
](https://opensource.org/licenses/MIT)

An interactive map viewer that overlays historical map tiles onto a modern base map, using a "spotlight" or "spyglass" effect to compare past and present geography. This project is a specific implementation of [retroscope](https://github.com/frogcat/retroscope) for the Sabae area.

## Demo

**Live Application:** **[http://fukuno.jig.jp/app/retroscope-sabae/](http://fukuno.jig.jp/app/retroscope-sabae/)**

See also the author's blog post: [http://fukuno.jig.jp/1333](http://fukuno.jig.jp/1333)

## Features

*   **Spotlight View:** Move your mouse (or tap on touch devices) to reveal a circular portion of a historical map layer over the current map. A crosshair marks the center of the spotlight.
*   **Dynamic Layer Availability:** The list of available historical maps updates automatically based on the current map viewport.
*   **Switchable Base Maps:** Toggle between modern GSI orthoimagery (satellite/aerial photos) and the standard GSI map.
*   **Vector Annotations:** Place names (towns and areas) are displayed as vector-based labels, which remain sharp at any zoom level.

## How It Works

The application is built with [Leaflet.js](https://leafletjs.com/) and uses several plugins to achieve its functionality:

*   The core spotlight effect is created using `leaflet-tileoverlay-mask`, which renders a tile layer within a specified radius of the cursor.
*   Base maps are standard `L.tileLayer` instances, managed by a `L.control.layers` switcher.
*   Historical overlay layers are defined in `layers.json` and dynamically loaded. The application checks for tile availability at the current map center and updates the UI accordingly.
*   Place name annotations are loaded from an experimental GSI vector tile service and rendered as `L.divIcon` markers.
*   The map's URL is updated with the current position and zoom level using `leaflet-hash`.

## Data Sources & Attribution

This project relies on map tiles and data from several sources. Please see the original sources for terms of use.

*   **Base Maps (背景地図タイル):**
    *   Source: Geospatial Information Authority of Japan (GSI) Tiles (地理院タイル)
    *   Attribution: [オルソ画像](http://maps.gsi.go.jp/development/ichiran.html#ort), [標準地図](http://maps.gsi.go.jp/development/ichiran.html#std) (国土地理院)

*   **Historical Overlay (前景地図タイル):**
    *   Source: GSI National Land Image Information (1st Phase, 1974-1978)
    *   Attribution: [国土画像情報 第一期1974～1978年撮影(地理院タイル)](http://maps.gsi.go.jp/development/ichiran.html#gazo1)

*   **Annotations (注記):**
    *   Source: GSI Experimental Vector Tiles
    *   Attribution: [注記(ベクトルタイル提供実験)](https://github.com/gsi-cyberjapan/experimental_anno/)

*   **Historical Availability Data ( NIAES ):**
    *   The original version utilized data from the Historical Agricultural Environment Browsing System.
    *   Source: [歴史的農業環境閲覧システム(NIAES)](http://habs.dc.affrc.go.jp/)

## Dependencies

*   [Leaflet.js](https://leafletjs.com/) (v1.0.0-beta.2)
*   [jQuery](https://jquery.com/)
*   [leaflet-tileoverlay-mask](https://github.com/frogcat/leaflet-tileoverlay-mask)
*   [Leaflet Hash](https://github.com/mlevans/leaflet-hash)

## Original Project

This repository is a fork and specific implementation of the original `retroscope` project by [@frogcat](https://github.com/frogcat).

*   **Original Repository:** **[https://github.com/frogcat/retroscope](https://github.com/frogcat/retroscope)**

## License

This project is licensed under the MIT License.