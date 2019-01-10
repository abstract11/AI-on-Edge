##########################
*matplotlib*
##########################


What is matplotlib?
Matplotlib is a Python 2D plotting library which produces publication quality figures in a variety of hardcopy formats and interactive environments across platforms.

What is it used for?
Matplotlib can be used in Python scripts, the Python and `IPython <http://ipython.org/>`_ shells, the `Jupyter notebook <https://jupyter.org/>`_, web application servers, and four graphical user interface toolkits.

Why matplotlib exist?
Matplotlib tries to make easy things easy and hard things possible.

What can matplotlib do?
You can generate plots, histograms, power spectra, bar charts, errorcharts, scatterplots, etc., with just a few lines of code.

Matplotlib Toolkits
=========================


* Basemap: It is a map plotting toolkit with various map projections, coastlines and political boundaries.

* Cartopy: It is a mapping library featuring object-oriented map projection definitions, and arbitrary point, line, polygon and image transformation capabilities.

* Excel tools: Matplotlib provides utilities for exchanging data with Microsoft Excel.

* Mplot3d: It is used for 3-D plots.

* Natgrid: It is an interface to the natgrid library for irregular gridding of the spaced data.

**Example**

* Code for sine wave:

 | import numpy as np
 | import matplotlib.pyplot as plt
 | # Compute the x and y coordinates for points on a sine curve 
 | x = np.arange(0, 3 * np.pi, 0.1)
 | y = np.sin(x)
 | plt.title("sine wave form")
 | # Plot the points using matplotlib 
 | plt.plot(x, y)
 | plt.show()

* Output:

.. image:: adityajupyter/matplot.png
	:width: 500px
	:align: center
	:height: 500px
	:alt: alternate text





