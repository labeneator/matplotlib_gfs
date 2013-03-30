matplotlib_gfs
==============

Matplotlib and the NOAA's Global Forecasting System
A quick intro on how to play around with GFS data using matplotlib.
Ideas come from:
* http://braz.blogspot.com/2009/12/r-for-global-climate-forecasting.html
* http://joewheatley.net/ncep-global-forecast-system/

Prerequisites
--------------
# Fetched data from NOAA.
    http://www.ftp.ncep.noaa.gov/data/nccf/com/gfs/prod/gfs.2013032712/
  Installed particular this dataset:
    http://www.ftp.ncep.noaa.gov/data/nccf/com/gfs/prod/gfs.2013032712/gfs.t12z.sfluxgrbf03.grib2

# Installed wgrib2:
  http://www.cpc.ncep-global-forecast-systemep.noaa.gov/products/wesley/wgrib2/index.html

# Extracted the fields I was interested in from the grib2 file into netcdf
./grib2/wgrib2/wgrib2  -s  gfs.t12z.sfluxgrbf03.grib2  | grep :LAND | ./grib2/wgrib2/wgrib2 -i gfs.t12z.sfluxgrbf03.grib2 -netcdf land.netcdf
./grib2/wgrib2/wgrib2  -s  gfs.t12z.sfluxgrbf03.grib2  | grep TMP:2 | ./grib2/wgrib2/wgrib2 -i gfs.t12z.sfluxgrbf03.grib2 -netcdf temp2.netcdf
./grib2/wgrib2/wgrib2  -s  gfs.t12z.sfluxgrbf03.grib2  | grep VEG: | ./grib2/wgrib2/wgrib2 -i gfs.t12z.sfluxgrbf03.grib2 -netcdf vegetation.netcdf
./grib2/wgrib2/wgrib2  -s  gfs.t12z.sfluxgrbf03.grib2  | grep TCDC: | ./grib2/wgrib2/wgrib2 -i gfs.t12z.sfluxgrbf03.grib2 -netcdf cloud.netcdf

# You can view the available fields using:
./grib2/wgrib2/wgrib2  -s  gfs.t12z.sfluxgrbf03.grib2  | less
  and visiting:
     http://www.nco.ncep.noaa.gov/pmb/products/gfs/gfs.t00z.sfluxgrbf00.grib2.shtml

