# Evaluation

This folder contains the scripts which clean the result data into multiple .txt files. Those .txt files are necessary for statistical test.

## Usage

### RQ1:
To evaluate the results for RQ1, please run the following commends in the path of this folder (Please note that you need to do these steps for each of the projects):

1. Firstly, running this script will generate .txt files for statistical test.
```
$ python3 eval_rq1.py -p [project name]
```

2. Secondly, to get the Scott-Knott analysis for the results, execute **sk_stats.py** by
```
$ cat rq1_tet_result.txt | python2 sk_stats.py --text 30 --latex True (for test execution time metric)
$ cat rq1_ms_result.txt | python2 sk_stats.py --text 30 --latex True (for mutation score metric)
```
  - The best approach for test execution time evaluation metric will be the approach in the **lowest rank** (minimize).
  - The best approach for mutation score evaluation metric will be the approach in the **highest rank** (maximize).

### RQ2 & RQ3:
To evaluate the results for RQ2 and RQ3, please run the following commends in the path of this folder (Please note that you need to do these steps for each of the projects):

1. Firstly, to find the best subset of objectives for NSGA-II, please run
```
$ python3 eval_nsga2_select.py
```
  Then use Scott-Knott analysis to find the best one by
```
$ cat nsga2_tet_result.txt | python2 sk_stats.py --text 30 --latex True (for test execution time metric)
$ cat nsga2_ms_result.txt | python2 sk_stats.py --text 30 --latex True (for mutation score metric)
```
  - The best subset for test execution time evaluation metric will be the combinations in the **lowest rank** (minimize).
  - The best subset for mutation score evaluation metric will be the combinations in the **highest rank** (maximize).

2. Secondly, to compare NSGA-II to our approach DoLesS, please run
```
$ python3 eval_rq23.py -p [project name]
```
  To find the best approach for RQ2, please execute **sk_stats.py** by
```
$ cat rq23_tet_result.txt | python2 sk_stats.py --text 30 --latex True (for test execution time objective)
$ cat rq2_derivative_result.txt | python2 sk_stats.py --text 30 --latex True (for discontinuity objective)
$ cat rq2_infinite_result.txt | python2 sk_stats.py --text 30 --latex True (for growth to infinity objective)
$ cat rq2_instability_result.txt | python2 sk_stats.py --text 30 --latex True (for instability objective)
$ cat rq2_minmax_result.txt | python2 sk_stats.py --text 30 --latex True (for difference of minimum and maxmum output objective)
```
  - The best approach for test execution time objective will be in the **lowest rank** (minimize).
  - The best approach for discontinuity objective will be in the **highest rank** (maximize).
  - The best approach for growth to infinity objective will be in the **highest rank** (maximize).
  - The best approach for instability objective will be in the **highest rank** (maximize).
  - The best approach for difference of minimum and maximum output objective will be in the **highest rank** (maximize).

  To find the best approach for RQ3, please execute **sk_stats.py** by
```
$ cat rq23_tet_result.txt | python2 sk_stats.py --text 30 --latex True (for test execution time evaluation metric)
$ cat rq3_ms_result.txt | python2 sk_stats.py --text 30 --latex True (for mutation score evaluation metric)
```
  - The best approach for test execution time evaluation metric will be the approach in the **lowest rank** (minimize).
  - The best approach for mutation score evaluation metric will be the approach in the **highest rank** (maximize).
