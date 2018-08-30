# iRODS-ETL-RailScanner
Metadata extraction, transformation and load scripts for the iRODS pilot Rail Scanner use case.

In this use case shipping containers are placed at strategic locations along the train tracks and fitted out with cameras: webcam, colour film and infrared. The recorded videos are transferred to the researcher using USB disks. The videos are then analysed to study freight activity.

The first notebook was set up by Scott Cunningham to transfer the video files to central storage, sorting them into collections representing train passing ‘events’. Susan Branchett later adapted this notebook to use iRODS as the central storage using [davrods](https://github.com/UtrechtUniversity/davrods) and to generate iRODS `imeta` commands that are then used to add metadata to the ‘event’ collections in iRODS.

During the pilot a GUI was developed for a different use case, see the [ImRODS repository](https://github.com/TU-Delft-ICT-Innovation/ImRODS). The second notebook was developed to make use of the GUI. It copies the first steps of the first notebook, but this times creates a screen shot from the middle of each .avi video, adding it to the iRODS collection. This is a sort of visual metadata that helps describe the video in the form of a .jpg image.

In the original loading of the data, timestamps consisting of date and time were loaded as one metadata item. The third notebook splits timestamps up into a date field and a time field. This time the iRODS Python API is used (instead of generating `imeta` commands) to remove the combined timestamps and add the separate date and time metadata items.

