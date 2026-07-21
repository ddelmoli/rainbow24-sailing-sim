# Rainbow 24 Sailing Simulator

A single-file browser sailing simulator: sail a **Sparkman & Stephens Rainbow 24** keelboat on the **Chesapeake Bay off Annapolis**, from the cockpit, in today's real wind. No installation, no build step, no accounts — open `index.html` and go.

> ## ⚠️ NOT FOR NAVIGATION
> This is a training toy. The physics are deliberately simplified, and the charted features, shorelines, depths, and aids to navigation are incomplete and may be out of date. **Never use it for real-world piloting.** Carry current official charts and publications.
>
> Not affiliated with or endorsed by the American Sailing Association, Sparkman & Stephens, or Tidewater Boats.

## What it does

**Sail from the cockpit.** The default view puts you on a cockpit seat with the boat heeling under you — the horizon tilts, not the boat. Switch seats between port and starboard (`X`), and look **port / forward / starboard** or crane **up at the rig** (`Q` `F` `E` `U`) to read the masthead Windex and the upper leech.

**Read the telltales, like on the real boat.**
- Paired red/green yarns on the jib luff
- Four telltales up the mainsail leech
- Red yarn on the port shrouds, green on starboard

Each one streams, flutters, stalls, or hangs limp based on the sail's actual angle of attack — so trimming by telltale works the way it does on the water.

**Sail the boat, not a menu.** Tiller, mainsheet, and both jib sheets, including **backing the jib** (`B`) to get out of irons. The tiller can be moved in absolute terms (arrow keys) or **relative to the sail** (`T` toward / `G` away) — the mapping flips automatically when the boom crosses, so "push the tiller toward the sail" means what your instructor means.

**Physics tuned to the boat.** Mass, sail area, and hull speed come from the real Rainbow 24 (24' LOA, 17'3" LWL, 2,250 lb, ~214 ft² sail area). Modeled: apparent wind, lift and stall by angle of attack, leeway, heel and its effect on drive, weather helm that builds as she heels, hull-speed drag, loss of steerage at low speed, being in irons and backing out of it, and crash jibes. Roughly 4 kn close-hauled and 5 kn on a beam reach in 12 knots of breeze.

**Real Annapolis.** Georeferenced shorelines from Tolly Point around to Sandy Point, with the Naval Academy chapel dome, the three Greenbury Point radio towers, the Severn River bridge, the Bay Bridge, and hazy Kent Island. A heading tape and horizon compass carry live bearings to each landmark.

**Real aids to navigation.** Buoy and beacon positions are pulled from **NOAA ENC Direct** — the electronic charts behind chart 12283 — and rendered by type: green cans, red nuns, lighted pillar buoys, pile beacons with triangular/square dayboards, the Spa Creek junction mark, and Triton Light. Chart labels appear when you get close. Includes the Annapolis Harbor channel, Spa Creek, Eastport, Lake Ogleton, Whitehall, and the Chesapeake Channel shipping buoys.

**Three weather modes** (real-time is the default):
- 🛰 **Real-time** — current observations from **Thomas Point Light (TPLM2)**, the NOAA station four miles south of the Roads, refreshed every 10 minutes. Falls back to Open-Meteo model data, then to holding the last conditions if you're offline.
- 🎚 **Simulated** — pick a wind speed and direction.
- 🎲 **Random** — shifts and builds on its own every minute or two.

**Two views.** Cockpit is the default; `V` toggles a god's-eye view with the telltale instrument panel, wake, and puff patches. In god's-eye, `M` cycles the background between stylized water, **satellite imagery**, and a **nautical chart**, and the mouse wheel zooms.

## Controls

| Key | Action |
| --- | --- |
| `←` `→` | Tiller, absolute — bow turns opposite |
| `F` / `G` | Tiller toward / away from the sail (flips automatically when the boom crosses) |
| `space` | Center the tiller |
| `Q` / `W` | Ease / trim the mainsheet |
| `Y` / `U` | Ease / trim the **port** jib sheet |
| `O` / `I` | Ease / trim the **starboard** jib sheet |
| `Z` | Back the jib (hold) |
| `H` / `J` | Sit port / starboard |
| `C` `V` `B` | Look port / forward / starboard |
| `T` | Look up at the masthead vane |
| `6` | Cockpit ⇄ god's eye |
| `5` | Cycle god's-eye map (water / satellite / chart) — wheel zooms |
| `M` | Wind and sail sound on / off |
| `P` | Pause |

### Sound

Off by default; press `M` or the sound button to start it (browsers require a click or keypress before any audio can play). Everything is synthesized with the Web Audio API — there are no sound files to download, and it still works offline.

The soundscape follows **apparent** wind, not true wind — so it is loudest close-hauled, where boat speed and true wind add together, and drops away as you bear off, going quietest on a run where you are sailing with the air mass. In 12 knots of true wind that spans roughly 15 knots apparent upwind down to 8 on a run: about a 9 dB swing, with the hiss through the rig falling several hundred Hz alongside it. Note that it tracks *heading*, not boat speed — a beam reach is the fastest point of sail but is quieter than close-hauled. Three layers: the low body of the wind, the higher hiss through the rig, and canvas flogging when a sail luffs, which flaps faster and louder as the breeze gets up. Head into the wind and you'll hear both sails break before you see them.

### Two jib sheets

The jib is trimmed by two independent sheets, as on the boat. Whichever one is to **leeward** is the working sheet and sets the sail's trim; the windward one lies lazy. Haul the windward sheet in while the leeward one is eased and the jib goes **aback** — which is how you back the jib to steer out of irons, and also what happens if you forget to release the old sheet during a tack. The sidebar labels each sheet *working* or *lazy* and warns when the sail is backed.

## Running it

Open `index.html` in any modern browser. Everything is in that one file.

Internet access is optional but adds the live weather and the satellite/chart map layers; offline, the simulator falls back to stylized water and holds the last known wind.

## Data sources and attribution

- **Aids to navigation** — [NOAA ENC Direct](https://encdirect.noaa.gov/) (public domain)
- **Live wind** — [NWS API](https://www.weather.gov/documentation/services-web-api) station TPLM2, with [Open-Meteo](https://open-meteo.com/) as a fallback
- **Satellite imagery** — Esri World Imagery
- **Chart tiles** — © [OpenStreetMap](https://www.openstreetmap.org/copyright) contributors; seamarks from [OpenSeaMap](https://www.openseamap.org/)
- **Boat specifications** — Sparkman & Stephens Rainbow 24, built by Tidewater Boats 1962–77

## License

[MIT](LICENSE).
