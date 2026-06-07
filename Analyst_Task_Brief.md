# Task Brief: Road Corridor Accessibility Analysis

We have two OSM layers for a residential area in the Netherlands (Tilburg region) —
building footprints (561 polygons) and a road network (43 lines), both in EPSG:4326.
I need you to run a corridor accessibility analysis in QGIS and package everything
neatly into a single deliverable folder.

Before doing anything, reproject both layers to EPSG:28992 (Amersfoort / RD New) so
all distance calculations are in metres — save these as buildings_28992.gpkg and
roads_28992.gpkg.

Buffer the road network into three concentric rings (50 m, 100 m, 150 m) and save
them as a single multi-ring layer called road_buffers_multiring.gpkg — not separate
files. Then compute the distance from every building centroid to its nearest road
segment. Use that distance to classify each building into one of four categories:
Directly Accessible (within 50 m), Moderately Accessible (50-100 m), Accessible
(100-200 m), or Isolated (beyond 200 m). Store the class and the raw distance as
attributes and save the result as buildings_classified.gpkg.

For outputs, I only want what matters: buildings_28992.gpkg, roads_28992.gpkg,
road_buffers_multiring.gpkg, and buildings_classified.gpkg. Nothing else. Load
everything into a single QGIS project, apply a clear categorised symbology to the
buildings (green through red by access class), and save the project as
Road_Corridor_Analysis.qgz so there are no broken links when the folder is moved.

Save everything — including a README.md documenting the methodology, output files,
and key findings — to the path I will share with you.

The deliverable is a clean, self-contained folder with 6 files total: 4 spatial
outputs, the project file, and the README. Nothing intermediate, nothing redundant.
