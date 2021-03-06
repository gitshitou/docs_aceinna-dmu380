************************************
Python-Based Serial-Message Decoder
************************************

.. contents:: Contents
    :local:
    
.. sectionauthor:: Joseph S Motyka <jmotyka at aceinna.com>


Creating a python-based decoder
================================

The first step to using the OpenIMU decoder and spooling tools, *python-openimu*, to properly
decode an output message is to define the message in the file *openimu.json*. For the “l1”
message, the following is added to the file:

::

    {
        "name": "l1",
        "description": "Leveler Output Message",
        "payload": [{
                "type": "uint32",
                "name": "timeCntr",
                "unit": "msec"
            },
            {
                "type": "double",
                "name": "time",
                "unit": "s"
            },
            {
                "type": "float",
                "name": "roll",
                "unit": "rad"
            },
            {
                "type": "float",
                "name": "pitch",
                "unit": "rad"
            },
            {
                "type": "float",
                "name": "xAccel",
                "unit": "m/s/s"
            },
            {
                "type": "float",
                "name": "yAccel",
                "unit": "m/s/s"
            },
            {
                "type": "float",
                "name": "zAccel",
                "unit": "m/s/s"
            }
        ],
            "graphs": [{
                "name": "Acceleration",
                "units": "m/s/s",
                "xAxis": "Time (s)",
                "yAxes": ["xAccel", "yAccel", "zAccel"],
                "colors": ["#FF0000", "#00FF00", "#0000FF"],
                "yMax": 80
            },
            {
                "name": "Attitude (Roll and Pitch)",
                "units": "deg",
                "xAxis": "Time (s)",
                "yAxes": ["roll", "pitch"],
                "colors": ["#FF0000", "#00FF00"],
                "yMax": 20
            }
        ]
    }


This information tells the decoder the order of the output data in the serial message, its type
(float, double, int, etc.), as well as the units associated with the data.  It also defines how the
data should be plotted, including axis-titles and colors.


.. note::

    A useful tool to check if the json-file is properly formatted is found at: https://jsonlint.com

