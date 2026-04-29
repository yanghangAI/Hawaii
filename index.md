# Hawaii Trip Plan — Group of 4 (Budget)

**Dates:** May 27 – June 4, 2026
**Flights:** HNL arrive 5/27 11:57 PM · HNL→KOA 5/31 2:40→3:29 PM · KOA depart 6/4 9:25 PM

## Trip Map

<link rel="stylesheet" href="https://unpkg.com/leaflet@1.9.4/dist/leaflet.css" integrity="sha256-p4NxAoJBhIIN+hmNHrzRCf9tD/miZyoHS5obTRR9BMY=" crossorigin="" />
<script src="https://unpkg.com/leaflet@1.9.4/dist/leaflet.js" integrity="sha256-20nQCchB9co0qIjJZRGuk2/Z9VM+kNiyxNV1lvTlZBo=" crossorigin=""></script>

<div id="trip-map" style="height: 520px; min-height: 520px; width: 100%; border-radius: 8px; margin: 1em 0;"></div>

<script>
window.addEventListener('load', function() {
  var map = L.map('trip-map');
  L.tileLayer('https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png', {
    maxZoom: 19,
    attribution: '&copy; OpenStreetMap'
  }).addTo(map);

  var oahuColor = '#1f77b4';
  var bigIslandColor = '#d62728';
  var flightColor = '#888';

  var oahu = [
    { name: 'HNL Airport (arrive 5/27 11:57 PM)', coords: [21.3187, -157.9224] },
    { name: 'Waikiki — lodging', coords: [21.2767, -157.8294] },
    { name: 'Diamond Head (5/28)', coords: [21.2620, -157.8055] },
    { name: 'Pearl Harbor / USS Arizona (5/29 AM)', coords: [21.3650, -157.9500] },
    { name: 'Haleiwa / North Shore (5/29 PM)', coords: [21.5928, -158.1033] },
    { name: 'Hanauma Bay (5/30)', coords: [21.2690, -157.6938] }
  ];

  var bigIsland = [
    { name: 'KOA Airport (arrive 5/31 3:29 PM)', coords: [19.7388, -156.0456] },
    { name: 'Kailua-Kona — lodging', coords: [19.6400, -155.9969] },
    { name: 'Hawaii Volcanoes NP (6/1)', coords: [19.4302, -155.2570] },
    { name: 'Punaluʻu Black Sand Beach', coords: [19.1356, -155.5050] },
    { name: 'Rainbow Falls, Hilo (6/2)', coords: [19.7194, -155.1097] },
    { name: 'Akaka Falls (6/2)', coords: [19.8533, -155.1531] },
    { name: 'Two Step / Hōnaunau (6/3)', coords: [19.4197, -155.9128] },
    { name: 'Hapuna Beach (6/4)', coords: [19.9931, -155.8253] },
    { name: 'Mauna Kea Visitor Station (6/4)', coords: [19.7607, -155.4561] }
  ];

  function addStops(stops, color) {
    stops.forEach(function(s, i) {
      L.circleMarker(s.coords, {
        radius: 7, color: color, fillColor: color, fillOpacity: 0.85, weight: 2
      }).bindPopup('<b>' + (i + 1) + '. ' + s.name + '</b>').addTo(map);
    });
  }

  addStops(oahu, oahuColor);
  addStops(bigIsland, bigIslandColor);

  L.polyline(oahu.map(function(s) { return s.coords; }), { color: oahuColor, weight: 3, opacity: 0.7 }).addTo(map);
  L.polyline(bigIsland.map(function(s) { return s.coords; }), { color: bigIslandColor, weight: 3, opacity: 0.7 }).addTo(map);
  L.polyline([oahu[0].coords, bigIsland[0].coords], {
    color: flightColor, weight: 2, opacity: 0.6, dashArray: '6, 8'
  }).bindPopup('Flight HNL → KOA, 5/31').addTo(map);

  var legend = L.control({ position: 'bottomright' });
  legend.onAdd = function() {
    var div = L.DomUtil.create('div');
    div.style.background = 'white';
    div.style.padding = '6px 10px';
    div.style.borderRadius = '6px';
    div.style.boxShadow = '0 1px 4px rgba(0,0,0,0.2)';
    div.style.fontSize = '13px';
    div.innerHTML =
      '<div><span style="display:inline-block;width:10px;height:10px;background:' + oahuColor + ';border-radius:50%;margin-right:6px;"></span>Oahu (5/27–5/31)</div>' +
      '<div><span style="display:inline-block;width:10px;height:10px;background:' + bigIslandColor + ';border-radius:50%;margin-right:6px;"></span>Big Island (5/31–6/4)</div>' +
      '<div><span style="display:inline-block;width:14px;height:0;border-top:2px dashed ' + flightColor + ';margin-right:6px;vertical-align:middle;"></span>Inter-island flight</div>';
    return div;
  };
  legend.addTo(map);

  var allCoords = oahu.concat(bigIsland).map(function(s) { return s.coords; });
  map.fitBounds(allCoords, { padding: [30, 30] });

  setTimeout(function() {
    map.invalidateSize();
    map.fitBounds(allCoords, { padding: [30, 30] });
  }, 250);
});
</script>

---

## Oahu (May 27 night → May 31 afternoon) — no car

**Why no car:** Waikiki parking runs $35–50/night and TheBus + walking covers everything. Get a HOLO card at any 7-Eleven: $3/ride, $7.50/day cap, $30/week cap.

### Lodging
- **Waikiki Beachside Hostel** or **Polynesian Hostel Beach Club** — private 4-bed rooms ~$150–200/night total. Walk to beach.
- Alternative: budget Airbnb in Waikiki/Ala Moana for 4.

### May 27 (arrival, late)
- Land 11:57 PM. Skip TheBus (late runs sparse). Split a Lyft/Uber to Waikiki (~$35–45 for 4).
- Crash.

### May 28 — Diamond Head + Waikiki
- **Sunrise Diamond Head hike** ($5/person, reservation REQUIRED at gostateparks.hawaii.gov — book NOW).
- Breakfast at **Diamond Head Market & Grill** or cheap loco moco at Rainbow Drive-In.
- Afternoon: Waikiki Beach, free hula at Kuhio Beach (check schedule).
- Dinner: **Marukame Udon** (~$8/person, line moves fast).

### May 29 — Pearl Harbor + North Shore (long day)
- Morning: **USS Arizona Memorial** (free; $1 reservation fee on recreation.gov — book 8 weeks ahead, otherwise try same-day walk-up at 7 AM).
- TheBus Route 20 from Waikiki → Pearl Harbor.
- Afternoon: Bus 52 to **North Shore** (~2 hr, but it's the cheap way). Eat at **Giovanni's Shrimp Truck** ($15) in Haleiwa, swim at Waimea Bay.
- Sunset bus back. Long day but free/cheap.

### May 30 — Snorkel + East side
- **Hanauma Bay** ($25/person, reservations open 48 hrs ahead at 7 AM HST sharp — set an alarm, slots vanish in seconds). Best snorkeling on Oahu. Bring own gear or rent on-site ($20).
- TheBus Route 22 from Waikiki direct.
- Or alternate (free): **Lanikai Pillbox** hike + Lanikai/Kailua Beach (Bus 67).
- Dinner: **Rainbow Drive-In** plate lunch.

### May 31 — light morning, fly out
- Walk Waikiki Beach, grab Leonard's malasadas.
- Lyft to HNL by 12:30 PM. Flight 2:40 PM.

---

## Big Island (May 31 evening → June 4 night)

### Rental Car
- **Book NOW** — Big Island prices spike close to date. Compare:
  - **Costco Travel** (best rates if anyone has membership)
  - **Discount Hawaii Car Rental** (aggregator, often beats direct)
  - **Turo** as backup
- Get an SUV or midsize — saddle road and Volcano park have rough patches but no 4WD needed for paved areas. Skip the 4WD upsell unless going to Mauna Kea summit.
- Pickup at KOA on arrival, return before 9:25 PM flight on 6/4.

### Lodging
- **Airbnb/VRBO in Kona** for all 4 nights (~$150–250/night for whole place beats 2 hotel rooms). Look at Kailua-Kona, Holualoa, or Captain Cook.
- Alternative: 2 nights Kona + 1 night near Volcano village to avoid one long drive day.

### Food/Money savers
- **Costco Kona** (membership required) — gas is cheapest on island, plus stock up on poke, rotisserie chicken, water.
- **Walmart Kona** for groceries if no Costco.
- Cook breakfast + pack lunch from Airbnb. Eat out 1 meal/day.

### May 31 — arrival
- Land 3:29 PM, pick up car, hit Costco/Walmart for groceries + gas.
- Sunset at **Magic Sands Beach** or **Kahalu'u Beach** (turtles).
- Easy dinner at Airbnb.

### June 1 — Hawaii Volcanoes National Park (full day)
- Leave Kona ~7 AM, ~2.5 hr drive via Hwy 11 (south route, more scenic).
- **Park entry $30/vehicle, valid 7 days.**
- Stops: Kīlauea Visitor Center → Crater Rim Drive → Steam Vents → Kīlauea Iki overlook → **Thurston Lava Tube** → Chain of Craters Road down to the sea arch.
- Pack lunch, fill gas in Volcano village.
- Stay past dark to see crater glow if Kīlauea is erupting (check nps.gov/havo for current activity).
- En route back: **Punalu'u Black Sand Beach** (sea turtles, often) if daylight, or save for next day.

### June 2 — Hilo side waterfalls + black sand
- Drive Saddle Road (Hwy 200) across to Hilo (~1.5 hr).
- **Rainbow Falls** (free, 5 min from parking).
- **Akaka Falls State Park** ($5/vehicle, 442-ft falls, easy loop).
- Lunch in Hilo: **Suisan Fish Market** poke bowls (~$12).
- **Punalu'u Black Sand Beach** on the way back via south route, or return via saddle.

### June 3 — Kona snorkel day
- **Two Step (Honaunau Bay)** — best shore snorkeling on island, free. Get there by 8 AM for parking + calm water.
- **Pu'uhonua o Hōnaunau** (Place of Refuge) next door, $20/vehicle.
- Afternoon: **Kealakekua Bay** lookout, or chill at Magic Sands.
- Sunset dinner: split a fish plate at **Da Poke Shack** or grab from Costco.

### June 4 — last day, late flight
- Morning: **Hapuna Beach** (one of best beaches in US, free, north of Kona ~45 min).
- OR **Mauna Kea Visitor Center** at 9,200 ft — free, sunset is incredible. Acclimatize 30 min. Don't drive to summit without 4WD/permit; the visitor center is enough.
- Return rental by ~7 PM, dinner at airport-area food, fly 9:25 PM.

---

## Rough Budget (per person, 4 ppl splitting)

| Item | Oahu | Big Island |
|---|---|---|
| Lodging | $40–60/night | $40–60/night |
| Transit/car | $15 total (HOLO + Lyft) | $80–120 (car + gas split) |
| Food | $40/day | $35/day |
| Activities | $30–60 total | $20–40 total |

**Per person estimate: ~$700–950 not counting flights.**

---

## Book / reserve right now (most time-sensitive)
1. **Diamond Head** entry — gostateparks.hawaii.gov
2. **USS Arizona Memorial** — recreation.gov (8 weeks out, going fast)
3. **Hanauma Bay** — pros7.hnl.info, opens 48 hrs ahead at 7 AM HST
4. **Big Island rental car** — Costco Travel / Discount Hawaii Car Rental
5. Lodging on both islands

## Things to skip (overrated for budget)
- Polynesian Cultural Center ($90+/person)
- Submarine tours
- Helicopter tours (unless this is your splurge)
- Luaus (~$150+/person — get cheap kalua pig at any plate lunch spot instead)
