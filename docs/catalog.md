---
layout: default
title: IPRD Catalog Documentation
nav_order: 4
---

# IPRD Catalog

The International Public Radio Directory (IPRD) provides access to thousands of radio stations from around the world, organized by country and genre.

## Available Playlists

IPRD offers several ways to access the radio station collection:

### Complete Playlist

The complete collection is available as a single M3U file:
- [All Stations (all_stations.m3u)](/site_data/all_stations.m3u)

### Country-Specific Playlists

Browse stations by country:

{% assign countries = site.data.summary.countries | sort: "name" %}
{% if countries.size > 0 %}
  <ul>
  {% for country in countries %}
    {% if country.count > 0 %}
    <li><strong>{{ country.name }}</strong> - <a href="/site_data/by_country/{{ country.code | downcase }}.m3u">{{ country.code }}.m3u</a> ({{ country.count }} stations)</li>
    {% endif %}
  {% endfor %}
  </ul>
{% else %}
  <p>Country data currently unavailable. Please check back later.</p>
{% endif %}

For a complete list of all data files organized in an easy-to-browse format, check our [Radio Data Files](./data_files.md) page.

## How to Use the Playlists

1. **Download** - Click on any playlist link to download the M3U file
2. **Open in Media Player** - Use a compatible player such as:
   - VLC Media Player
   - Winamp
   - iTunes
   - Most mobile media players

3. **Stream** - Enjoy radio from around the world!

## Technical Information

Each playlist follows the standard M3U format with extended information:

```
#EXTM3U
#EXTINF:-1 tvg-logo="https://example.com/logo.png" group-title="News;Talk",Station Name
https://example.com/stream.mp3
```

The `group-title` field contains genre information, and the `tvg-logo` field contains a URL to the station's logo.

## API Access

For developers, we provide JSON access to our catalog data. See the [API Documentation](/api/) for more information on programmatic access to IPRD data.