# Published link audit — August 24, 2026

Site checked: <https://kulpojke.github.io/nr218/>

## Summary

- Crawled 52 published HTML pages; every page used as a crawl seed loaded successfully.
- Checked 712 link occurrences representing 194 unique targets, including internal pages, anchors, local downloads, and external links.
- Found eight definite source locations to fix: one missing download, five dead external URLs, and two invalid calendar anchors.
- `assets/toy_data.zip` was the only published file download that returned `404`. The other explicit ZIP, CSV, GeoJSON, PDF, TIFF, and spreadsheet download links encountered by the crawler loaded successfully or redirected successfully.
- Reveal.js navigation fragments such as `#/1/7` were excluded because they are slide routes, not ordinary HTML anchors.

## Definite broken links

### Missing local download

- [ ] [src/lab_01_computers.qmd:30](src/lab_01_computers.qmd#L30)
  - Published on: <https://kulpojke.github.io/nr218/lab_01_computers.html>
  - Link: `assets/toy_data.zip`
  - Published target: <https://kulpojke.github.io/nr218/assets/toy_data.zip>
  - Result: `404 Not Found`.

### External links returning 404

- [ ] [src/finding_gis_data.qmd:81](src/finding_gis_data.qmd#L81)
  - Published on `finding_gis_data.html` and the combined `index.html` slides.
  - Link: <https://landsat.gsfc.nasa.gov/wp-content/uploads/2015/06/Landsat.v.Sentinel-2.png>
  - Result: `404 Not Found`.

- [ ] [src/finding_gis_data.qmd:217](src/finding_gis_data.qmd#L217)
  - Published on `finding_gis_data.html` and the combined `index.html` slides.
  - Link: <https://awesome-ee-spectral-indices.readthedocs.io/en/latest/index.html#expressions>
  - Result: `404 Not Found`.

- [ ] [src/intro_geospatial_data.qmd:74](src/intro_geospatial_data.qmd#L74)
  - Published on `intro_geospatial_data.html` and the combined `index.html` slides.
  - Link: <https://data.ca.gov/dataset/ca-perimeters-cal-fire-nifc-firis-public-view>
  - Result: `404 Not Found`.

- [ ] [src/spatial_data_models.qmd:173](src/spatial_data_models.qmd#L173)
  - Published on `spatial_data_models.html` and the combined `index.html` slides.
  - Link: <https://upload.wikimedia.org/wikipedia/commons/c/3/Kelvin_og_Celsius_temperaturskalaer.png>
  - Result: `404 Not Found`. The local image used on line 170 is present; only its external source link is broken.

- [ ] [src/lab_02_first_map.md:73](src/lab_02_first_map.md#L73)
  - Published on: <https://kulpojke.github.io/nr218/lab_02_first_map.html>
  - Link: <https://www.qgistutorials.com/en/docs/3/basic_vector_styling.htm>
  - Result: `404 Not Found`.

### Invalid internal anchors

- [ ] [src/syllabi/section_07_fall_2026.qmd:37](src/syllabi/section_07_fall_2026.qmd#L37)
  - Current link: `#spring-term-calendar-2026`
  - Result: the anchor does not exist on the Section 07 page.
  - Current rendered calendar anchor: `#section-07---fall-term-calendar-2026`.

- [ ] [src/syllabi/section_09_fall_2026.qmd:37](src/syllabi/section_09_fall_2026.qmd#L37)
  - Current link: `#spring-term-calendar-2026`
  - Result: the anchor does not exist on the Section 09 page.
  - Current rendered calendar anchor: `#section-09---fall-term-calendar-2026`.

## Manual checks recommended

These are not classified as definitely broken because the target may require authentication, reject automated requests, or have been temporarily unavailable.

### Google spreadsheet returned 401

- [ ] [src/intro_excel_arc.qmd:165](src/intro_excel_arc.qmd#L165)
  - Link: <https://docs.google.com/spreadsheets/d/19QFK3faJuigk_8Nc8smDpe2k-U62ID3f0B-4wgm93tg/edit?gid=0#gid=0>
  - Automated result: `401 Unauthorized`. Check the sharing permissions in a private/incognito browser window.

### BeiDou CSNO/TARC timed out

- [ ] [src/gps.qmd:129](src/gps.qmd#L129)
  - Link: <https://www.csno-tarc.cn/status/introductionEn?lang=en>
  - Automated result: TLS handshake timeout.

### Sites that rejected the automated checker

- [ ] [src/what_is_gis.qmd:138](src/what_is_gis.qmd#L138)
  - Link: <https://gis.stackexchange.com/questions/3083/seeking-examples-of-beautiful-maps>
  - Automated result: `403 Forbidden`; this is commonly caused by bot protection.

- [ ] ResearchGate link — automated result: `403 Forbidden`; check manually:
  - [src/syllabus.qmd:77](src/syllabus.qmd#L77)
  - [src/syllabi/section_07_fall_2026.qmd:69](src/syllabi/section_07_fall_2026.qmd#L69)
  - [src/syllabi/section_09_fall_2026.qmd:69](src/syllabi/section_09_fall_2026.qmd#L69)
  - [src/syllabi/syllabus_spring_2026_s03.qmd:68](src/syllabi/syllabus_spring_2026_s03.qmd#L68)
  - [src/syllabi/syllabus_spring_2026_s05.qmd:68](src/syllabi/syllabus_spring_2026_s05.qmd#L68)
  - Link: <https://www.researchgate.net/publication/392560878_Your_Brain_on_ChatGPT_Accumulation_of_Cognitive_Debt_when_Using_an_AI_Assistant_for_Essay_Writing_Task>

### Intermittent server response

- [ ] Spatial Thoughts course link — returned `503 Service Unavailable` during the concurrent crawl, then `200 OK` on immediate direct recheck. No fix is currently indicated, but recheck if students report trouble:
  - [src/syllabus.qmd:100](src/syllabus.qmd#L100)
  - [src/syllabi/section_07_fall_2026.qmd:92](src/syllabi/section_07_fall_2026.qmd#L92)
  - [src/syllabi/section_09_fall_2026.qmd:92](src/syllabi/section_09_fall_2026.qmd#L92)
  - [src/syllabi/syllabus_spring_2026_s03.qmd:91](src/syllabi/syllabus_spring_2026_s03.qmd#L91)
  - [src/syllabi/syllabus_spring_2026_s05.qmd:91](src/syllabi/syllabus_spring_2026_s05.qmd#L91)
  - Link: <https://courses.spatialthoughts.com/>

## Audit limitations

- Results describe the published site as it appeared on August 24, 2026. Unpushed local pages and links are outside this audit.
- A successful response confirms that a target loaded; it does not confirm that the downloaded dataset is the intended version or contains the expected files.
- Links requiring Cal Poly, Google, SharePoint, or other account authentication may need a manual check in an incognito window and again while signed in as a student.
