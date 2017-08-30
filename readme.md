dopplerscript is a command-line tool to input satellite doppler shifts into a gnuradio
flowgraph. The [doppler.py](https://github.com/rxcomm/dopplerscript/blob/master/doppler.py)
script replaces [gpredict](https://github.com/csete/gpredict)
as the source for doppler frequency updates in
[gr-gpredict-doppler](https://github.com/wnagele/gr-gpredict-doppler), making
it easy to script satellite reception.

Requirements:
     [gr-gpredict-doppler](https://github.com/wnagele/gr-gpredict-doppler),
     [pyephem](https://github.com/brandon-rhodes/pyephem)

I have also included a command-line flowgraph based on the classic one by
[otti-soft](https://github.com/otti-soft/meteor-m2-lrpt) which will receive
Meteor M2 LRPT transmissions. This version of the flowgraph includes the
[gr-gpredict-doppler](https://github.com/wnagele/gr-gpredict-doppler) modifications
required to use the doppler updates from
[doppler.py](https://github.com/rxcomm/dopplerscript/blob/master/doppler.py)
(or [gpredict](https://github.com/csete/gpredict)).

Usage: I usually run the
[rtlsdr_doppler_m2_lrpt_rx_nogui.py](https://github.com/rxcomm/dopplerscript/blob/master/rtlsdr_doppler_m2_lrpt_rx_nogui.py)
script using [timeout](http://manpages.ubuntu.com/manpages/trusty/man1/timeout.1.html)
as follows:

     timeout <satpass_duration> rtlsdr_doppler_m2_lrpt_rx_nogui.py <filename> <pll_alpha>

e.g.

     timeout 932 rtlsdr_doppler_m2_lrpt_rx_nogui.py meteor_20170831_1632 .012

where 932 is the duration of the satellite pass, meteor_20170831_1632 is the filename
prefix for the soft symbol file, and 0.012 is the loop bandwidth of the Costas Loop in the
flowgraph.

You should also be sure to change your location data and the pointer to the satellite
TLE data in the doppler.py file.
