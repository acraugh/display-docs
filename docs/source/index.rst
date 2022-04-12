############################
Display Namespace User Guide
############################

This document supplies basic information for understanding and using the Display Discipline 
namespace in PDS4 product labels.

.. contents::
   :backlinks: top

***************************
Summary
***************************

The *Display* namespace is used to define how an array-type object with two or more dimensions 
should be displayed on, for example, a video screen. The 
namespace also provides classes to identify color bands for display of a color image, and 
timing information to display an image cube as a movie.

To use the Display namespace, include the `<Display_Settings>` class in the `<Discipline_Area>`
of your PDS4 observational product label. The `<Display_Orientation>` subclass is always
required to be present to identify the 2D image plane and how it should be displayed so that 
other classes and documentation can reliably refer to directions like "up", "left", and 
"clockwise".

At a Glance
=======================

:Namespace: Display
:Namespace Type: Discpline
:Prefix: disp
:Top-Level Class: `Display_Settings`
:Used with:
    - `Array_2D_Image`
    - `Array_3D_Image`
    - `Array_3D_Movie`
    - Any array object with two or more axes that can be visualized as an image
:Steward: - Trent Hare 
          - Cartography and Image Science Node, USGS
          - **thareUSGS** on Github
          - *thare@usgs.gov*
:Repo: https://github.com/pds-data-dictionaries/ldd-disp


***************************
Terminology
***************************

This section describes terminology specific to the Display namespace descriptions.

Bands
=======================

In the Display class and attribute descriptions "bands" refer to subscripts along one of the
axes of an array with three or more dimentions. This axis is identified as the *color_axis*
or *band axis*. A color/band axis may have many more than three elements. The 
`<Color_Display_Settings>` class is used to identify three subscripts along that axis to 
serve as "red", "green", and "blue" for the purposes of visualization.

Movie
=======================

In the context of an observational product file, a *movie* is a sequence of images intended
to be displayed at some regular interval. the `<Movie_Display_Settings>` class identifies 
the "time" axis and suggested parameters for playback.
 
***************************
Usage Notes
***************************

The `<Display_Settings>` class will 
generally be required to be present for any array-type data objects with two or more 
dimensions. Image display is a basic visualization tool that reviewers frequently like
to have available, and the `Display_Settings` class supports that. Although the class
is not currently required by PDS4 core schema constraints, nodes and reviewers will 
likely impose the requirement if `Display_Settings` is omitted.

Under the current design, if you have multiple image data objects described by a single
label, a separate `<Display_Settings>` class will be required for each, even if the
settings are identical. Each `Display_Settings` class is associated with a specific
array-type object through the required `<pds:Local_Internal_Identifier>` class. This 
means you array classes need to include the (optional) `<local_identifier>` attribute.
The value of each `<local_identifier>` must be unique. 

The Display namespace identifies axes in the corresponding array by their `<axis_name>`
values. Spelling and case both count.

Dependencies
=======================

The Display namespace classes do not depend on any other discipline namespace classes being
present in the product label.

***************************
Templates
***************************

***************************
Examples
***************************
