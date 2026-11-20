# IPTV – a Couchmate plugin

Live TV with a programme guide, movies and series from Dispatcharr (Xtream). Search, reminders, the next episode and a merged programme guide.

- **Live TV** with a programme guide, also guessed from the channel name for channels that have none (event
  channels such as "PPV [18:50 Team A - Team B]").
- **Movies** open an info page with **Play**, **Continue from …** and **Start over**.
- **Series** show their seasons and episodes. Watched episodes are ticked off, and the one you are in the middle of
  can be continued or started over. "Next episode" shows 10 s before the end, and the next one follows straight on.
- **Search** across channels, movies and series. The catalogue is read at start and refreshed in the background.

**Requires:** Dispatcharr (https://github.com/Dispatcharr/Dispatcharr), reachable from the Couchmate server, with an Xtream user.

## Install

In the Couchmate admin panel, open **Plugins**: it is listed under **Get plugins** – press **Install**, then switch
it on and fill in its settings.

## Updates

The server checks this repository for new releases every 6 hours. Under **Plugins** you can update with one
click, or switch on **Update automatically** to have new versions installed by themselves. They wait until
nobody is watching.

To release a new version: raise `version` in `plugin.json`, commit, and publish a GitHub release tagged
`v<version>` (e.g. `v2.0.1`).

## Settings

- **Dispatcharr address** – How the Couchmate server reaches Dispatcharr. In Docker, e.g. http://dispatcharr:9191 or http://host.docker.internal:9191.
- **Xtream user** – Create a user in Dispatcharr.
- **Xtream password**
- **Stream mode**
- **Public Dispatcharr address** – Only for direct mode: the address the apps use to reach Dispatcharr.
- **Shared movie download** – Movies and episodes are fetched once and shared with everyone – only one provider connection. Needs proxy mode.
- **File type for live channels**
- **Catalogue cache (seconds)**
- **Merged guide: primary guide (XMLTV link)** – Your provider's XMLTV. Empty = no merged guide. Point Dispatcharr's EPG source at /plugins/iptv/epg/merged.xml.gz?pin=<PIN>.
- **Merged guide: fallback for countries** – "auto" = the countries of your channels, or e.g. "se,no".
- **Merged guide: fallback source per country** – {CC} is replaced by the country code, e.g. SE.
- **Merged guide: extra fallback sources** – More XMLTV links, separated by commas.
- **Merged guide: manual channel mappings** – primaryid=fallbackid, separated by commas.
- **Merged guide: rebuild every (hours)**
- **Guide from channel names when there is none** – Only for channels with no programme information at all – a real guide always wins.
- **Time zone of the times in channel names** – For event channels with a time in their name, e.g. Europe/Stockholm.

## Making your own

Plugins are plain JavaScript modules – `index.mjs` here is a working example to start from.
