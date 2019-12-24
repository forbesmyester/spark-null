# spark-null

Tiny wrapper around [https://github.com/holman/spark](spark) which allows adding "n" to represent null values. This allows drawing graphs like:

```bash
$ echo '6 1 4 n 4' | ./spark-null
█▁▅ ▅
```

Instead of what normal `spark` will do:

```bash
$ echo '6 1 4 0 4' | spark
█▂▅▁▅
```

You can also use a `-0` switch to leave empty spaces where 0's are as well:

```bash
$ echo '6 1 4 0 4' | spark-null -0
█▁▅ ▅
```

This sometimes tells a more accurate story.

Because `spark-null` supports minimum and maximum values you can draw positive and negative graphs relatively easily.

```bash
J1S=$(echo "2 5 2 0 0 0 0 2 4" | ./spark-null -0 -m 0 -n 9)
J1F=$(echo "0 0 0 2 9 5 1 0" | ./spark-null -i -m 0 -n 9)
J2S=$(echo "1 0 0 0 3 1 0 1 0" | ./spark-null -0 -m 0 -n 9)
J2F=$(echo "0 3 5 9 2 5 3 0 6" | ./spark-null -i -m 0 -n 9)
echo -e "\nImportant Monitored Job:\n  SUCCESS:  \e[32m${J1S}\e[0;0m\n  FAILURE:  \e[30;41m${J1F}\e[0;0m\n\n\nBuggy Job We Don't Care About:\n  SUCCESS:  \e[32m${J2S}\e[0;0m\n  FAILURE:  \e[30;41m${J2F}\e[0;0m\n"
```

![pos-neg.png](./pos-neg.png)

License: MIT
