:warning: experimental biodiversity data archive

# umsp-cmpc

This archive contains records related to the University of Minnesota Insect Collection https://insectcollection.umn.edu/ . This collection contains over 4M specimen mounted on slides, stuck on pins, or stored in viles. 

As an example, a [log of collection transactions from a 2021 CMPC archive](./umsp-cmpc-transactions-up-to-2021.csv) (see also [umsp-cmpc-transactions-up-to-2021.csv](./umsp-cmpc-transactions-up-to-2021.csv) was generated using:

```
$ git clone https://github.com/jhpoelen/umsp-cmpc
$ cd umsp-cmpc
$ preston ls\
 | grep "2021"\
 | preston dbase2json\
 | grep FAMILY\
 | grep ORDER\
 | grep TRAN\
 | grep DATE\
 | mlr --ijson --ocsv cat\
 > umsp-cmpc-transactions-up-to-2021.csv
```

where:
  * [git](https://git-scm.com/) (https://git-scm.com/) is content tracker
  * [preston](https://preston.guoda.bio) (https://preston.guoda.bio) is a biodiversity dataset tracker
  * [grep](https://en.wikipedia.org/wiki/Grep) (https://en.wikipedia.org/wiki/Grep) is a standard posix/linux commandline tool
  * [mlr](https://miller.readthedocs.io/en/latest/) (aka "miller", https://miller.readthedocs.io/en/latest/) is a csv/json processing tool 


With this, the following [sorted list of unique order-family pairs](./umsp-cmpc-order-families-up-to-2021.csv) (see also [umsp-cmpc-order-families-up-to-2021.csv](./umsp-cmpc-order-families-up-to-2021.csv)) was generated:

```
 cat umsp-cmpc-transactions-up-to-2021.csv\
 | mlr --csv cut -f ORDER,FAMILY\
 | mlr --csv uniq -g ORDER,FAMILY\
 > umsp-cmpc-order-families-up-to-2021.csv
```


