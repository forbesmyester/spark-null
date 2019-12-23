# spark-null

Tiny wrapper around [https://github.com/holman/spark](spark) which allows adding "n" to represent null values. This allows drawing graphs like:

    $ echo '6 1 4 n 4' | ./spark-null
    █▁▅ ▅

Instead of what normal `spark` will do:

    $ echo '6 1 4 0 4' | spark
    █▂▅▁▅

You can also use a `-0` switch to leave empty spaces where 0's are as well:

    $ echo '6 1 4 0 4' | spark-null -0
    █▁▅ ▅

This sometimes tells a more accurate story.

License: MIT
