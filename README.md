# PLUVAR

### Interactive map of New Caledonia rainfall diurnal cycles at:

[https://rawgit.com/nicolasfauchereau/PLUVAR/master/www/index.html](https://rawgit.com/nicolasfauchereau/PLUVAR/master/www/index.html) (updated)

or:

[https://cdn.rawgit.com/nicolasfauchereau/PLUVAR/master/www/map.html](https://cdn.rawgit.com/nicolasfauchereau/PLUVAR/master/www/map.html) (cached)

### percentage of variance explained by the 1st 2 harmonics

![var explained](https://raw.githubusercontent.com/nicolasfauchereau/PLUVAR/master/figures/map_var_explained_2harm.png "variance explained")

### time of the diurnal cycle maximum

![max](https://raw.githubusercontent.com/nicolasfauchereau/PLUVAR/master/figures/position_max_diurnal_cycle.png "diurnal cycle maximum")

### Affinity Propagation clustering on the seasonal variations in the diurnal cycle

The seasonal variations in the diurnal cycle of precipitation (precipitation amounts)
are first calculated for each of the stations, as illustrated by the image below: the left plot present the precipitation amount (in mm) while for the right plot, the diurnal precipitation is normalised by the month's average. It shows that e.g. for ME PARA (see location below)


![MEPARA](https://raw.githubusercontent.com/nicolasfauchereau/PLUVAR/master/figures/MEPARA.png "MEPARA")

the diurnal precipitation maximum occurs towards the end of the afternoon (~ 16 PM local time) during the summer (December - March). During the cool season (~ March - August), the precipitation is sparse, but in relative terms it tends to occur early in the morning (around 5 AM) and to some extent in the beginning of the night, although the signal is quite noisy.

![heatmap](https://raw.githubusercontent.com/nicolasfauchereau/PLUVAR/master/figures/heatmap_month_hour_98803006.png "heatmap")

The idea is to use clustering methods to group together stations which present similar patterns of seasonal / diurnal variations.

[Affinity Propagation (AP)](https://en.wikipedia.org/wiki/Affinity_propagation) is a clustering method based on *message passing* between data points. Unlike clustering algorithms such as *k*-means or *k*-medoids, AP does not require the number of clusters to be determined or estimated before running the algorithm. Like *k*-medoids, AP finds **exemplars**, or members of the original dataset that are representative of clusters (i.e. the *archetype*).

The original reference is [Brendan J. Frey and Delbert Dueck. Clustering by Passing Messages Between Data Points. Science, vol 315, pages 972-976, 2007.](http://science.sciencemag.org/content/315/5814/972)

AP is performed on respectively the total precipitation (in mm, left hand figure above) and the precipitation relative to the month average (right hand figure above)

#### clustering on the filtered values (1st 2 harmonics)

![AP](https://raw.githubusercontent.com/nicolasfauchereau/PLUVAR/master/figures/classif_6clusters_AP_f.png "AP filtered")

#### clustering on the filtered values (1st 2 harmonics) normalized by the month's average

![AP](https://raw.githubusercontent.com/nicolasfauchereau/PLUVAR/master/figures/classif_5clusters_AP_f_d.png "AP filtered / normalized")

<hr size=100>

### comparison with TRMM 3B42 Satellite estimates (in progress)

The 3-hourly Satellite estimates (00Z, 03Z, 09Z, 12Z, 15Z, 18Z, 21Z) are available from:

ftp://disc2.nascom.nasa.gov/data/TRMM/Gridded/3B42_V7
