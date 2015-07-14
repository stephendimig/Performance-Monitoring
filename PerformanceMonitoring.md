Performance Monitoring Using Ganglia
========================================================
author: Stephen Dimig
date: Mon Jul 13 20:36:03 2015
transition: rotate



Ganglia 
========================================================
Ganglia is a scalable distributed system monitor tool for high-performance computing systems such as clusters and grids.

- *Ganglia Monitoring Daemon (gmond)* Runs on the node being monitored. Gathers metric data through a extensible python script.
- *Ganglia Meta Daemon (gmetad)* Runs on the Ganglia server. Collects forwarded data and stores it in the RRD.
- *Ganglia PHP Web Front-end* Runs on the Ganglia server. Provides a view of the gathered information via real-time dynamic web pages.
- *RRD* Realtime database for storage of Ganglia metrics.
- *Ganglia* is distributed under BSD license

R-Studio
========================================================
RStudio is a free and open source integrated development environment (IDE) for R, a programming language for statistical computing and graphics.
- *R* is a programming language for statistical computing and graphics. 
- *Knitr*  is an engine for dynamic report generation with R. It is a package in R that enables integration of R code into reports (ie; you can include code and data in the same report template).
- *R Mardown* is a  lightweight markup language with plain text formatting syntax designed so that it can be converted to HTML.
- *RStudio* is distributed under the GNU General Public License

VE-DSR Performance Monitoring 
========================================================

![alt text](system-diagram.gif)

PSBR
========================================================
The Ganglia Monitoring Daemon (gmond) runs on the PSBR. It periodically gathers metric data and forwards it to the Ganglia Web server through the NO which acts as a relay.

- *gmond.conf* is a configuration file in /etc/ganglia/gmod.conf. It contains information that gmond requires to run.
- *psbr.py* is a python script that is used to gather all of the psbr related metrics. The gmond daemon will periodically invoke this script. It contians definitions for all of the metrics including a function to invoke and it's type.
- *psbr.pyconf* this file contains the name of each metric defined in psbr.py above plus a title that will be displayed by the web interface.


NO
========================================================
The Ganglia Monitoring Daemon (gmond) runs on the PSBR but it acts only as a relay forwarding data from the PSBRs to the Ganglia server. All of our lab metrics currently go through the same NO.

- *gmond.conf* is a configuration file in /etc/ganglia/gmod.conf. It contains information that gmond requires to run.


Ganglia Web Server
========================================================
The Ganglia Web Server runs the Ganglia Meta Daemon (gmetad) and Ganglia PHP Web Front-end. We run this on an old G6 card in the lab. It has more extensive RPMs installed on it than a client.

- *rrd2csv.py* Ganglia stores metric data from the monitored nodes in an RRD database. RRD has a binary format and is laid out with one metric per file. The rrd2csv.py allows you to generate a csv file from the RRD data so you can do more detailed analysis on it.


Ganglia PSBR CPU Example
========================================================

![alt text](ganglia_cpu.png)


Ganglia PSBR Session Recs Example
========================================================

![alt text](ganglia_session_recs.png)


Your PC
========================================================
You can do analysis on the CSV file for a performance run on your loacal PC using Excel or R-Studio. I prefer the second option because it easier. You can generate a report for a new run by just changing out the csv file and hitting a single button.

- *psbr.Rmd* the R-markdown file that is a template for a perfomance analysis report.
- *psbr.Rpres* you can also do interactive presentations of the report data using a charting package like googleVis or rCharts.

Dynamic Report Generation
========================================================
R-Studio offers dynamic report generation through knitr which is a package that enables integration of R code into reports (ie; you can include code and data in the same report template).

- *Knitr* allows R code and documentation to exist in the same file so that changing the data results in a whole new report.
- *R Mardown* is a  lightweight markup language with plain text formatting syntax designed so that it can be converted to HTML.
- *psbr.Rmd* Template of a perfomance analysis report for PSBR.

The following graphs are the type of thing you might see in a dynamic report using R-Studio. Note you can also do statistical analysis on the data. Dynamic reports are great for comparing runs with different configurations, etc.

Example Table
========================================================

| __Resource__  | __Value__  |
| ------------------------- | -------- |
| Start                    :| 07/02/2015 09:59:30 |
| End                      :| 07/02/2015 11:06:45 |
| Duration                 :| 1.12 Hours |
| RAM Start                :| 60.74 % |
| RAM End                  :| 60.75 % |
| RAM Minimum              :| 60.73 % |
| RAM Maximum              :| 61.04 % |
| RAM Average              :| 60.87 % |
| CPU Usage                :| 15.9 % |
| Number Bindings - Mean   :| 7889770.37|
| Ingress Stack Event Rate :| 8854.34 |
| Egress Stack Event Rate  :| 10859.51 |

Example CPU Analysis
========================================================

![plot of chunk unnamed-chunk-2](PerformanceMonitoring-figure/unnamed-chunk-2-1.png) 


Example Database Composition
========================================================

![plot of chunk unnamed-chunk-3](PerformanceMonitoring-figure/unnamed-chunk-3-1.png) 


Example ComAgent Stack Event Rates
========================================================


![plot of chunk unnamed-chunk-4](PerformanceMonitoring-figure/unnamed-chunk-4-1.png) 

Dynamic Presentation Generation
========================================================
R-Studio offers dynamic presentation generation through the R-Presenation package that enables integration of R code into presentations (ie; you can include code and data in the same presentation template).

- *R Presentation* allows R code and documentation to exist in the same file so that changing the data results in a whole new presentation.
- *R Mardown* is a  lightweight markup language with plain text formatting syntax designed so that it can be converted to HTML.
- *R Mardown* is a  lightweight markup language with plain text formatting syntax designed so that it can be converted to HTML.
- *psbr.Rpres* Template of a dynamic presentation for PSBR.
- *Interactive Charts* R Presentaion has support for interactive charts through rCharts or GoogleVis.

Example googleVis chart
========================================================

<!-- LineChart generated in R 3.1.2 by googleVis 0.5.8 package -->
<!-- Mon Jul 13 20:36:07 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataLineChartID15ce659dbdcb5 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 new Date(2015,6,2,9,59,30),
12.43 
],
[
 new Date(2015,6,2,9,59,45),
12.43 
],
[
 new Date(2015,6,2,10,0,0),
12.43 
],
[
 new Date(2015,6,2,10,0,15),
12.09 
],
[
 new Date(2015,6,2,10,0,30),
11.92 
],
[
 new Date(2015,6,2,10,0,45),
11.92 
],
[
 new Date(2015,6,2,10,1,0),
11.92 
],
[
 new Date(2015,6,2,10,1,15),
12.19333333 
],
[
 new Date(2015,6,2,10,1,30),
12.33 
],
[
 new Date(2015,6,2,10,1,45),
12.33 
],
[
 new Date(2015,6,2,10,2,0),
12.33 
],
[
 new Date(2015,6,2,10,2,15),
12.33 
],
[
 new Date(2015,6,2,10,2,30),
13.92133333 
],
[
 new Date(2015,6,2,10,2,45),
14.5 
],
[
 new Date(2015,6,2,10,3,0),
14.5 
],
[
 new Date(2015,6,2,10,3,15),
14.5 
],
[
 new Date(2015,6,2,10,3,30),
14.07466667 
],
[
 new Date(2015,6,2,10,3,45),
13.92 
],
[
 new Date(2015,6,2,10,4,0),
13.92 
],
[
 new Date(2015,6,2,10,4,15),
13.92 
],
[
 new Date(2015,6,2,10,4,30),
13.92 
],
[
 new Date(2015,6,2,10,4,45),
13.92 
],
[
 new Date(2015,6,2,10,5,0),
13.92 
],
[
 new Date(2015,6,2,10,5,15),
13.92 
],
[
 new Date(2015,6,2,10,5,30),
13.92 
],
[
 new Date(2015,6,2,10,5,45),
13.86866667 
],
[
 new Date(2015,6,2,10,6,0),
13.85 
],
[
 new Date(2015,6,2,10,6,15),
13.85 
],
[
 new Date(2015,6,2,10,6,30),
13.85 
],
[
 new Date(2015,6,2,10,6,45),
13.85 
],
[
 new Date(2015,6,2,10,7,0),
13.608 
],
[
 new Date(2015,6,2,10,7,15),
13.52 
],
[
 new Date(2015,6,2,10,7,30),
13.52 
],
[
 new Date(2015,6,2,10,7,45),
13.52 
],
[
 new Date(2015,6,2,10,8,0),
13.358 
],
[
 new Date(2015,6,2,10,8,15),
13.25 
],
[
 new Date(2015,6,2,10,8,30),
13.25 
],
[
 new Date(2015,6,2,10,8,45),
13.25 
],
[
 new Date(2015,6,2,10,9,0),
13.892 
],
[
 new Date(2015,6,2,10,9,15),
14.32 
],
[
 new Date(2015,6,2,10,9,30),
14.32 
],
[
 new Date(2015,6,2,10,9,45),
14.32 
],
[
 new Date(2015,6,2,10,10,0),
14.32 
],
[
 new Date(2015,6,2,10,10,15),
13.96066667 
],
[
 new Date(2015,6,2,10,10,30),
13.83 
],
[
 new Date(2015,6,2,10,10,45),
13.83 
],
[
 new Date(2015,6,2,10,11,0),
13.83 
],
[
 new Date(2015,6,2,10,11,15),
16.096 
],
[
 new Date(2015,6,2,10,11,30),
16.92 
],
[
 new Date(2015,6,2,10,11,45),
16.92 
],
[
 new Date(2015,6,2,10,12,0),
16.92 
],
[
 new Date(2015,6,2,10,12,15),
16.92 
],
[
 new Date(2015,6,2,10,12,30),
16.99333333 
],
[
 new Date(2015,6,2,10,12,45),
17.02 
],
[
 new Date(2015,6,2,10,13,0),
17.02 
],
[
 new Date(2015,6,2,10,13,15),
17.02 
],
[
 new Date(2015,6,2,10,13,30),
17.02 
],
[
 new Date(2015,6,2,10,13,45),
19.94 
],
[
 new Date(2015,6,2,10,14,0),
21.4 
],
[
 new Date(2015,6,2,10,14,15),
21.4 
],
[
 new Date(2015,6,2,10,14,30),
21.4 
],
[
 new Date(2015,6,2,10,14,45),
20.51266667 
],
[
 new Date(2015,6,2,10,15,0),
20.19 
],
[
 new Date(2015,6,2,10,15,15),
20.19 
],
[
 new Date(2015,6,2,10,15,30),
20.19 
],
[
 new Date(2015,6,2,10,15,45),
20.19 
],
[
 new Date(2015,6,2,10,16,0),
20.238 
],
[
 new Date(2015,6,2,10,16,15),
20.25 
],
[
 new Date(2015,6,2,10,16,30),
20.25 
],
[
 new Date(2015,6,2,10,16,45),
20.25 
],
[
 new Date(2015,6,2,10,17,0),
15.72533333 
],
[
 new Date(2015,6,2,10,17,15),
14.08 
],
[
 new Date(2015,6,2,10,17,30),
14.08 
],
[
 new Date(2015,6,2,10,17,45),
14.08 
],
[
 new Date(2015,6,2,10,18,0),
14.08 
],
[
 new Date(2015,6,2,10,18,15),
14.102 
],
[
 new Date(2015,6,2,10,18,30),
14.11 
],
[
 new Date(2015,6,2,10,18,45),
14.11 
],
[
 new Date(2015,6,2,10,19,0),
14.11 
],
[
 new Date(2015,6,2,10,19,15),
13.92333333 
],
[
 new Date(2015,6,2,10,19,30),
13.83 
],
[
 new Date(2015,6,2,10,19,45),
13.83 
],
[
 new Date(2015,6,2,10,20,0),
13.83 
],
[
 new Date(2015,6,2,10,20,15),
13.73 
],
[
 new Date(2015,6,2,10,20,30),
13.68 
],
[
 new Date(2015,6,2,10,20,45),
13.68 
],
[
 new Date(2015,6,2,10,21,0),
13.68 
],
[
 new Date(2015,6,2,10,21,15),
13.68 
],
[
 new Date(2015,6,2,10,21,30),
14.11333333 
],
[
 new Date(2015,6,2,10,21,45),
14.33 
],
[
 new Date(2015,6,2,10,22,0),
14.33 
],
[
 new Date(2015,6,2,10,22,15),
14.33 
],
[
 new Date(2015,6,2,10,22,30),
13.72866667 
],
[
 new Date(2015,6,2,10,22,45),
13.51 
],
[
 new Date(2015,6,2,10,23,0),
13.51 
],
[
 new Date(2015,6,2,10,23,15),
13.51 
],
[
 new Date(2015,6,2,10,23,30),
13.51 
],
[
 new Date(2015,6,2,10,23,45),
13.672 
],
[
 new Date(2015,6,2,10,24,0),
13.78 
],
[
 new Date(2015,6,2,10,24,15),
13.78 
],
[
 new Date(2015,6,2,10,24,30),
13.78 
],
[
 new Date(2015,6,2,10,24,45),
13.81333333 
],
[
 new Date(2015,6,2,10,25,0),
13.83 
],
[
 new Date(2015,6,2,10,25,15),
13.83 
],
[
 new Date(2015,6,2,10,25,30),
13.83 
],
[
 new Date(2015,6,2,10,25,45),
13.83 
],
[
 new Date(2015,6,2,10,26,0),
13.776 
],
[
 new Date(2015,6,2,10,26,15),
13.74 
],
[
 new Date(2015,6,2,10,26,30),
13.74 
],
[
 new Date(2015,6,2,10,26,45),
13.74 
],
[
 new Date(2015,6,2,10,27,0),
13.656 
],
[
 new Date(2015,6,2,10,27,15),
13.6 
],
[
 new Date(2015,6,2,10,27,30),
13.6 
],
[
 new Date(2015,6,2,10,27,45),
13.6 
],
[
 new Date(2015,6,2,10,28,0),
13.6 
],
[
 new Date(2015,6,2,10,28,15),
18.538 
],
[
 new Date(2015,6,2,10,28,30),
21.83 
],
[
 new Date(2015,6,2,10,28,45),
21.83 
],
[
 new Date(2015,6,2,10,29,0),
21.83 
],
[
 new Date(2015,6,2,10,29,15),
20.942 
],
[
 new Date(2015,6,2,10,29,30),
20.35 
],
[
 new Date(2015,6,2,10,29,45),
20.35 
],
[
 new Date(2015,6,2,10,30,0),
20.35 
],
[
 new Date(2015,6,2,10,30,15),
20.35 
],
[
 new Date(2015,6,2,10,30,30),
20.26466667 
],
[
 new Date(2015,6,2,10,30,45),
20.19 
],
[
 new Date(2015,6,2,10,31,0),
20.19 
],
[
 new Date(2015,6,2,10,31,15),
20.19 
],
[
 new Date(2015,6,2,10,31,30),
19.896 
],
[
 new Date(2015,6,2,10,31,45),
19.56 
],
[
 new Date(2015,6,2,10,32,0),
19.56 
],
[
 new Date(2015,6,2,10,32,15),
19.56 
],
[
 new Date(2015,6,2,10,32,30),
19.56 
],
[
 new Date(2015,6,2,10,32,45),
23.592 
],
[
 new Date(2015,6,2,10,33,0),
27.12 
],
[
 new Date(2015,6,2,10,33,15),
27.12 
],
[
 new Date(2015,6,2,10,33,30),
27.12 
],
[
 new Date(2015,6,2,10,33,45),
20.73133333 
],
[
 new Date(2015,6,2,10,34,0),
13.43 
],
[
 new Date(2015,6,2,10,34,15),
13.43 
],
[
 new Date(2015,6,2,10,34,30),
13.43 
],
[
 new Date(2015,6,2,10,34,45),
13.43 
],
[
 new Date(2015,6,2,10,35,0),
13.69133333 
],
[
 new Date(2015,6,2,10,35,15),
13.99 
],
[
 new Date(2015,6,2,10,35,30),
13.99 
],
[
 new Date(2015,6,2,10,35,45),
13.99 
],
[
 new Date(2015,6,2,10,36,0),
13.962 
],
[
 new Date(2015,6,2,10,36,15),
13.92 
],
[
 new Date(2015,6,2,10,36,30),
13.92 
],
[
 new Date(2015,6,2,10,36,45),
13.92 
],
[
 new Date(2015,6,2,10,37,0),
14.00666667 
],
[
 new Date(2015,6,2,10,37,15),
14.18 
],
[
 new Date(2015,6,2,10,37,30),
14.18 
],
[
 new Date(2015,6,2,10,37,45),
14.18 
],
[
 new Date(2015,6,2,10,38,0),
14.18 
],
[
 new Date(2015,6,2,10,38,15),
14.188 
],
[
 new Date(2015,6,2,10,38,30),
14.2 
],
[
 new Date(2015,6,2,10,38,45),
14.2 
],
[
 new Date(2015,6,2,10,39,0),
14.2 
],
[
 new Date(2015,6,2,10,39,15),
14.19 
],
[
 new Date(2015,6,2,10,39,30),
14.17 
],
[
 new Date(2015,6,2,10,39,45),
14.17 
],
[
 new Date(2015,6,2,10,40,0),
14.17 
],
[
 new Date(2015,6,2,10,40,15),
14.17 
],
[
 new Date(2015,6,2,10,40,30),
14.442 
],
[
 new Date(2015,6,2,10,40,45),
14.85 
],
[
 new Date(2015,6,2,10,41,0),
14.85 
],
[
 new Date(2015,6,2,10,41,15),
14.85 
],
[
 new Date(2015,6,2,10,41,30),
14.54 
],
[
 new Date(2015,6,2,10,41,45),
13.92 
],
[
 new Date(2015,6,2,10,42,0),
13.92 
],
[
 new Date(2015,6,2,10,42,15),
13.92 
],
[
 new Date(2015,6,2,10,42,30),
13.95666667 
],
[
 new Date(2015,6,2,10,42,45),
14.03 
],
[
 new Date(2015,6,2,10,43,0),
14.03 
],
[
 new Date(2015,6,2,10,43,15),
14.03 
],
[
 new Date(2015,6,2,10,43,30),
14.03 
],
[
 new Date(2015,6,2,10,43,45),
16.894 
],
[
 new Date(2015,6,2,10,44,0),
24.77 
],
[
 new Date(2015,6,2,10,44,15),
24.77 
],
[
 new Date(2015,6,2,10,44,30),
24.77 
],
[
 new Date(2015,6,2,10,44,45),
24.77 
],
[
 new Date(2015,6,2,10,45,0),
24.02 
],
[
 new Date(2015,6,2,10,45,15),
21.02 
],
[
 new Date(2015,6,2,10,45,30),
21.02 
],
[
 new Date(2015,6,2,10,45,45),
21.02 
],
[
 new Date(2015,6,2,10,46,0),
21.02 
],
[
 new Date(2015,6,2,10,46,15),
21.02 
],
[
 new Date(2015,6,2,10,46,30),
21.02 
],
[
 new Date(2015,6,2,10,46,45),
21.02 
],
[
 new Date(2015,6,2,10,47,0),
21.02 
],
[
 new Date(2015,6,2,10,47,15),
20.876 
],
[
 new Date(2015,6,2,10,47,30),
19.94 
],
[
 new Date(2015,6,2,10,47,45),
19.94 
],
[
 new Date(2015,6,2,10,48,0),
19.94 
],
[
 new Date(2015,6,2,10,48,15),
19.98133333 
],
[
 new Date(2015,6,2,10,48,30),
20.56 
],
[
 new Date(2015,6,2,10,48,45),
20.56 
],
[
 new Date(2015,6,2,10,49,0),
20.56 
],
[
 new Date(2015,6,2,10,49,15),
20.56 
],
[
 new Date(2015,6,2,10,49,30),
20.13466667 
],
[
 new Date(2015,6,2,10,49,45),
14.18 
],
[
 new Date(2015,6,2,10,50,0),
14.18 
],
[
 new Date(2015,6,2,10,50,15),
14.18 
],
[
 new Date(2015,6,2,10,50,30),
14.164 
],
[
 new Date(2015,6,2,10,50,45),
14.1 
],
[
 new Date(2015,6,2,10,51,0),
14.1 
],
[
 new Date(2015,6,2,10,51,15),
14.1 
],
[
 new Date(2015,6,2,10,51,30),
14.1 
],
[
 new Date(2015,6,2,10,51,45),
13.978 
],
[
 new Date(2015,6,2,10,52,0),
13.49 
],
[
 new Date(2015,6,2,10,52,15),
13.49 
],
[
 new Date(2015,6,2,10,52,30),
13.49 
],
[
 new Date(2015,6,2,10,52,45),
13.678 
],
[
 new Date(2015,6,2,10,53,0),
14.43 
],
[
 new Date(2015,6,2,10,53,15),
14.43 
],
[
 new Date(2015,6,2,10,53,30),
14.43 
],
[
 new Date(2015,6,2,10,53,45),
14.43 
],
[
 new Date(2015,6,2,10,54,0),
13.828 
],
[
 new Date(2015,6,2,10,54,15),
11.42 
],
[
 new Date(2015,6,2,10,54,30),
11.42 
],
[
 new Date(2015,6,2,10,54,45),
11.42 
],
[
 new Date(2015,6,2,10,55,0),
12.02533333 
],
[
 new Date(2015,6,2,10,55,15),
13.69 
],
[
 new Date(2015,6,2,10,55,30),
13.69 
],
[
 new Date(2015,6,2,10,55,45),
13.69 
],
[
 new Date(2015,6,2,10,56,0),
13.69 
],
[
 new Date(2015,6,2,10,56,15),
13.62666667 
],
[
 new Date(2015,6,2,10,56,30),
13.5 
],
[
 new Date(2015,6,2,10,56,45),
13.5 
],
[
 new Date(2015,6,2,10,57,0),
13.5 
],
[
 new Date(2015,6,2,10,57,15),
13.5 
],
[
 new Date(2015,6,2,10,57,30),
13.5 
],
[
 new Date(2015,6,2,10,57,45),
13.5 
],
[
 new Date(2015,6,2,10,58,0),
13.5 
],
[
 new Date(2015,6,2,10,58,15),
13.58666667 
],
[
 new Date(2015,6,2,10,58,30),
13.76 
],
[
 new Date(2015,6,2,10,58,45),
13.76 
],
[
 new Date(2015,6,2,10,59,0),
13.76 
],
[
 new Date(2015,6,2,10,59,15),
13.76 
],
[
 new Date(2015,6,2,10,59,30),
16.80333333 
],
[
 new Date(2015,6,2,10,59,45),
22.89 
],
[
 new Date(2015,6,2,11,0,0),
22.89 
],
[
 new Date(2015,6,2,11,0,15),
22.89 
],
[
 new Date(2015,6,2,11,0,30),
22.89 
],
[
 new Date(2015,6,2,11,0,45),
22.23333333 
],
[
 new Date(2015,6,2,11,1,0),
20.92 
],
[
 new Date(2015,6,2,11,1,15),
20.92 
],
[
 new Date(2015,6,2,11,1,30),
20.92 
],
[
 new Date(2015,6,2,11,1,45),
20.64666667 
],
[
 new Date(2015,6,2,11,2,0),
20.1 
],
[
 new Date(2015,6,2,11,2,15),
20.1 
],
[
 new Date(2015,6,2,11,2,30),
20.1 
],
[
 new Date(2015,6,2,11,2,45),
20.1 
],
[
 new Date(2015,6,2,11,3,0),
20.17 
],
[
 new Date(2015,6,2,11,3,15),
20.31 
],
[
 new Date(2015,6,2,11,3,30),
20.31 
],
[
 new Date(2015,6,2,11,3,45),
20.31 
],
[
 new Date(2015,6,2,11,4,0),
16.09666667 
],
[
 new Date(2015,6,2,11,4,15),
7.67 
],
[
 new Date(2015,6,2,11,4,30),
7.67 
],
[
 new Date(2015,6,2,11,4,45),
7.67 
],
[
 new Date(2015,6,2,11,5,0),
7.67 
],
[
 new Date(2015,6,2,11,5,15),
10.708 
],
[
 new Date(2015,6,2,11,5,30),
14.18 
],
[
 new Date(2015,6,2,11,5,45),
14.18 
],
[
 new Date(2015,6,2,11,6,0),
14.18 
],
[
 new Date(2015,6,2,11,6,15),
14.40866667 
],
[
 new Date(2015,6,2,11,6,30),
14.67 
],
[
 new Date(2015,6,2,11,6,45),
14.67 
] 
];
data.addColumn('datetime','Date');
data.addColumn('number','Cpu');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartLineChartID15ce659dbdcb5() {
var data = gvisDataLineChartID15ce659dbdcb5();
var options = {};
options["allowHtml"] = true;
options["height"] =    500;
options["width"] =    800;

    var chart = new google.visualization.LineChart(
    document.getElementById('LineChartID15ce659dbdcb5')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartLineChartID15ce659dbdcb5);
})();
function displayChartLineChartID15ce659dbdcb5() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartLineChartID15ce659dbdcb5"></script>
 
<!-- divChart -->
  
<div id="LineChartID15ce659dbdcb5" 
  style="width: 800; height: 500;">
</div>


Example googleVis bar chart
========================================================
<!-- BarChart generated in R 3.1.2 by googleVis 0.5.8 package -->
<!-- Mon Jul 13 20:36:07 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataBarChartID15ce6431ba8f1 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "ImsiApnAnchor",
7888134.16 
],
[
 "MsisdnAlt",
7888134.16 
],
[
 "MsisdnApnAlt",
7593975.93 
],
[
 "Ipv6AltV2",
7534017.817 
] 
];
data.addColumn('string','Type');
data.addColumn('number','Value');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartBarChartID15ce6431ba8f1() {
var data = gvisDataBarChartID15ce6431ba8f1();
var options = {};
options["allowHtml"] = true;
options["height"] =    500;
options["width"] =    800;

    var chart = new google.visualization.BarChart(
    document.getElementById('BarChartID15ce6431ba8f1')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartBarChartID15ce6431ba8f1);
})();
function displayChartBarChartID15ce6431ba8f1() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartBarChartID15ce6431ba8f1"></script>
 
<!-- divChart -->
  
<div id="BarChartID15ce6431ba8f1" 
  style="width: 800; height: 500;">
</div>

Example googleVis pie chart
========================================================
<!-- PieChart generated in R 3.1.2 by googleVis 0.5.8 package -->
<!-- Mon Jul 13 20:36:07 2015 -->


<!-- jsHeader -->
<script type="text/javascript">
 
// jsData 
function gvisDataPieChartID15ce6439a6b24 () {
var data = new google.visualization.DataTable();
var datajson =
[
 [
 "ImsiApnAnchor",
7888134.16 
],
[
 "MsisdnAlt",
7888134.16 
],
[
 "MsisdnApnAlt",
7593975.93 
],
[
 "Ipv6AltV2",
7534017.817 
] 
];
data.addColumn('string','Type');
data.addColumn('number','Value');
data.addRows(datajson);
return(data);
}
 
// jsDrawChart
function drawChartPieChartID15ce6439a6b24() {
var data = gvisDataPieChartID15ce6439a6b24();
var options = {};
options["allowHtml"] = true;
options["height"] =    500;
options["width"] =    800;

    var chart = new google.visualization.PieChart(
    document.getElementById('PieChartID15ce6439a6b24')
    );
    chart.draw(data,options);
    

}
  
 
// jsDisplayChart
(function() {
var pkgs = window.__gvisPackages = window.__gvisPackages || [];
var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
var chartid = "corechart";
  
// Manually see if chartid is in pkgs (not all browsers support Array.indexOf)
var i, newPackage = true;
for (i = 0; newPackage && i < pkgs.length; i++) {
if (pkgs[i] === chartid)
newPackage = false;
}
if (newPackage)
  pkgs.push(chartid);
  
// Add the drawChart function to the global list of callbacks
callbacks.push(drawChartPieChartID15ce6439a6b24);
})();
function displayChartPieChartID15ce6439a6b24() {
  var pkgs = window.__gvisPackages = window.__gvisPackages || [];
  var callbacks = window.__gvisCallbacks = window.__gvisCallbacks || [];
  window.clearTimeout(window.__gvisLoad);
  // The timeout is set to 100 because otherwise the container div we are
  // targeting might not be part of the document yet
  window.__gvisLoad = setTimeout(function() {
  var pkgCount = pkgs.length;
  google.load("visualization", "1", { packages:pkgs, callback: function() {
  if (pkgCount != pkgs.length) {
  // Race condition where another setTimeout call snuck in after us; if
  // that call added a package, we must not shift its callback
  return;
}
while (callbacks.length > 0)
callbacks.shift()();
} });
}, 100);
}
 
// jsFooter
</script>
 
<!-- jsChart -->  
<script type="text/javascript" src="https://www.google.com/jsapi?callback=displayChartPieChartID15ce6439a6b24"></script>
 
<!-- divChart -->
  
<div id="PieChartID15ce6439a6b24" 
  style="width: 800; height: 500;">
</div>

Client Installation
========================================================

- You can find a gzip file with a client insallation at ~dimig/Public/ganglia.
- Scp the gzip file to the target machine
- Uncompress the archive: gunzip ganglia.rpms.tar.gz
- Untar the archive file: tar xvf ganglia.rpms.tar
- This will create an rpms driectory that will include all of the required ganglia rpms plus some important files.
- Run the install.sh script: install.sh
- This will install all of the rpms, copy the files to where they need to be, and retart the gmond and httpd servers.
- All metric data will be forwarded to the Ganglia server at http://100.64.149.71/ganglia. 
