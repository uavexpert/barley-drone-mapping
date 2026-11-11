# Winter Barley Drone Mapping — RGB Vigor Map

A low-cost drone mapping project: flying a sub-250 g drone over a 4 ha winter barley field, processing the images into an orthophoto, and building a VARI vegetation index map to show crop vigor — using only free, open-source software.

## The field

- **Crop:** Winter barley, autumn tillering stage
- **Location:** Near Wrestedt, Uelzen, Germany (52.9157, 10.5719)
- **Area:** ~4 ha
- **Flight date:** 7 November 2026

## Flight

- **Drone:** DJI Mini 3 (sub-250 g) with RC-N1 controller
- **App:** Litchi Pilot (automated grid mission)
- **Altitude:** 45 m, speed 4 m/s
- **Overlap:** 80% front / 75% side
- **Photos:** 294 captured
- **Camera:** 48 MP, ISO 800, 1/640 s (foggy conditions)

## Processing

- **Software:** WebODM (open source) + QGIS
- **GCPs:** 5 ground control points, RMS 0.15 m
- **Output:** Georeferenced orthophoto (EPSG:32632, UTM 32N), ~5 cm GSD
- **Fix:** The first orthophoto came out bent (curved outline). Straightened in QGIS Georeferencer using Thin Plate Spline warp onto a satellite basemap.

## VARI vegetation index

VARI (Visible Atmospherically Resistant Index) highlights green vegetation using only RGB bands — no multispectral camera needed.

**Formula (Gitelson et al. 2002):**

```
VARI = (Green − Red) / (Green + Red − Blue)
```

Calculated in QGIS Raster Calculator from the orthophoto bands.

## Results

- **VARI range:** ~0.1–0.2 across the field (typical for barley at tillering)
- **Pattern:** Mostly uniform green-yellow (healthy, establishing crop). Tramlines show as red (bare soil). No large dead or bare patches.
- **Conclusion:** The crop is healthy and fairly uniform at this stage. The low-cost RGB drone + VARI workflow clearly separates crop from soil and shows real vigor variation across the field.

## What this proves

A €500 sub-250 g drone + free software (WebODM, QGIS) can produce a usable crop vigor map — no expensive multispectral sensor needed. The same workflow will be repeated in spring 2027 (stem elongation) to track how the pattern changes.

## Tools

- DJI Mini 3 + Litchi Pilot
- WebODM (photogrammetry)
- QGIS (mapping, VARI, georeferencing)
- Python (optional, for repeatable processing)

## Next steps

- Spring 2027 flight (stem elongation) — crosshatch pattern + visible ground markers to prevent the bend at the source
- Compare autumn vs. spring VARI
- Add ground truth (SPAD, biomass) for validation
