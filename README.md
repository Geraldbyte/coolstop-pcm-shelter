# CoolStop: PCM Bus Shelter

**A bus shelter roof and bench infused with a natural wax that absorbs heat as it melts — keeping commuters cooler with no electricity and no moving parts.**

Team 06 · RSE3106 SEP2 · James Dyson Award 2026 (Singapore)

---

## The problem

Singapore bus stops can exceed comfortable temperatures during long waiting periods. Standard shelter materials — sheet metal roofs, plastic and metal benches — heat up immediately under solar load and radiate that heat back at waiting commuters. Existing cooling trials at Singapore bus stops (Airbitat, Sol-Cool, LTA fan trials) all rely on **active** cooling: fans, misting, or refrigerant systems that need power, maintenance, and ongoing energy cost, which limits how widely they can scale across the bus stop network.

## What CoolStop does

CoolStop integrates a sealed **phase-change material (PCM)** panel — a coconut wax and palm wax blend — into the shelter roof and bench.

As ambient and solar heat raises the panel temperature, the wax absorbs that energy by **melting** rather than simply heating up (latent heat absorption). While the wax is melting, the panel surface holds a lower, near-constant temperature — the *melt plateau* — instead of climbing the way bare metal or plastic does. The blend's melting point is tuned to sit close to typical hot-weather ambient temperatures in Singapore, so it activates during the hottest parts of the day and re-solidifies overnight, ready for the next day.

**No power source. No pump. No moving parts. No consumables.**

## How it works (the physics)

1. **Sensible heating** — In a conventional shelter, absorbed heat goes directly into raising the surface temperature.
2. **Latent heat absorption** — In a PCM panel, once the wax reaches its melt onset temperature, incoming heat is spent breaking the solid structure of the wax instead of raising its temperature.
3. **Melt plateau** — The panel surface holds close to the melt temperature until the wax has fully melted, keeping the roof and bench cooler for longer during peak heat.
4. **Overnight recovery** — After sunset, the wax releases the stored heat and re-solidifies, resetting the cycle for the next day.

This is the same phenomenon that keeps a glass of ice water at 0 °C while the ice melts — shifted to a melting point useful at bus-stop temperatures.

## Why this material

We considered and ruled out several alternatives before settling on the coconut/palm wax blend:

| Concept | Why it was ruled out |
|---|---|
| Mist fans (solar-powered pump) | Already trialled in Singapore (Airbitat, Sol-Cool); active system with power + maintenance burden |
| Sun-tracking reflective panels | Physical limitations under HDB shadow conditions; moving parts |
| Electrochromic smart glass | True electrochromic film unsourceable locally (only PDLC available) |
| Venturi / thermal-chimney shelter geometry | Undermined by Singapore's humidity and low wind conditions |
| Salt-hydrate PCM (sodium sulfate decahydrate) | Unsourceable locally in a usable form |
| **Coconut + palm wax PCM blend** ✅ | **Locally sourceable (multi-day SG delivery), deployment-grade rather than proxy material, melting point in the useful range** |

Local sourcing was a hard requirement from our supervisor: the prototype must use deployment-grade materials, not laboratory proxies.

## Design process

1. **Concept exploration** — surveyed active cooling approaches (misting, reflective tracking, electrochromic glazing, chimney-effect geometry) and eliminated each on sourcing feasibility or physical limitations under Singapore conditions.
2. **Phenomenon selection** — pivoted from *moving heat away* to *absorbing heat in place* via latent heat, inspired by the constant temperature of melting ice.
3. **Material selection** — confirmed a coconut/palm wax blend with local sourcing and a melting point near hot-weather ambient temperature.
4. **Track 1: material characterisation** — side-by-side outdoor testing of a sealed wax panel against an identical control panel under direct sun, with paired sensors logging surface temperature every 15 seconds (see Field test results below).
5. **Track 2: shelter design** — SolidWorks model using standard Singapore bus stop dimensions, with PCM cavity thickness finalised once Track 1 results confirmed the material behaviour.

## Field test results (5 July 2026)

Two identical panel housings — one containing the sealed coconut/palm wax blend, one empty control — were placed side by side under direct early-afternoon sun in Singapore, with surface temperatures logged every 15 seconds by paired sensors on a microcontroller datalogger (~20.5 minutes, 83 paired readings).

| Metric | Result |
|---|---|
| Peak control panel surface temperature | 50.7 °C |
| Peak PCM panel surface temperature | **41.6 °C (9.1 °C cooler)** |
| PCM advantage across the heating phase | 6.4–10.6 °C cooler (mean 8.5 °C) |
| PCM heating rate below ~40 °C | 0.88 °C/min |
| PCM heating rate above ~40 °C | 0.20 °C/min — slowdown consistent with melt onset |
| Cooldown behaviour | PCM cooled more slowly and crossed the control at ~15 min, releasing stored latent heat (needed for overnight reset) |
| Independent spot-check | IR thermometer read 51.1 °C on the control side, matching the logged 50.7 °C peak |

**Raw data:** [`testing/field-test-2026-07-05.csv`](testing/field-test-2026-07-05.csv) · **Photo:** [`media/field-test-photo.jpg`](media/field-test-photo.jpg) · **Video:** [`media/field-test-video.mp4`](media/field-test-video.mp4)

*Honest caveat: the control panel was already warmer at the first logged reading, so we lead with the peak-to-peak comparison, which is unaffected by starting conditions.*

## How it's different

| | Active trials (Airbitat, Sol-Cool, LTA fans) | CoolStop |
|---|---|---|
| Energy input | Electricity required | None |
| Moving parts | Fans / pumps | None |
| Consumables | Water (misting) / refrigerant | None |
| Ongoing cost | Power + maintenance | Passive material, minimal upkeep |
| Scalability | Limited by infrastructure per stop | Panel swap into existing shelter forms |

## Roadmap

- Complete Track 1 heat-lamp / thermocouple characterisation (melt onset, plateau, differential, recovery)
- Finalise PCM cavity thickness in the SolidWorks shelter model
- Build a full-scale prototype panel
- Outdoor field testing under real sun exposure
- Validate day–night thermal cycling (full overnight re-solidification on consecutive hot days)
- Approach LTA / transport operators for a live bus stop pilot

## Repository structure

```
├── README.md          # This document
├── index.html         # Project website (GitHub Pages)
├── cad/               # SolidWorks shelter model
├── testing/           # Field test data (CSV, 15 s interval logs)
└── media/             # Field test photo, video, and poster frame
```

## Team

Team 06 — RSE3106 SEP2, Singapore.

## License

Documentation and media in this repository are shared for the purposes of the James Dyson Award 2026 submission. Contact the team before reuse.
