---
tags:
  - code
  - code_snippet
keywords: 
topics: 
language: 
date of note: 2024-04-08
---

## Code Snippet Summary




## Code

```bash
#!/bin/sh
PROGRAM=/apollo/env/RFUGE/perl-scripts/generateData.pl
ORG=1
OUTDIR="/home/$USER/work/data" 
## This data set is very big, just pull one day.
SERVICE="CASOrderEvaluation"
chmod g+w $OUTDIR

if [ $# -lt 2 ]
then
echo "To pull var of orders in a day."
echo "The 2nd Var is the start date"
echo "The 3rd Var is the end date"

else
SDAY=$1
EDAY=$2
OUTBASE="COEall"
OUT="$OUTDIR/$OUTBASE$SDAY-$EDAY-$ORG.csv"
SIG="$OUTDIR/$OUTBASE$SDAY-$EDAY-$ORG.sig"
#QUERY='$CONC_DREAMS_RULE_ID!="" && $CONC_DREAMS_RULE_ID!=4196550' # This is sample filter condition one should change. 
echo "Output to "$OUT

if [ -e "$OUT" ]; then
sudo \rm $OUT
fi

if [ -e "$SIG" ]; then
sudo \rm $SIG
fi 

touch $OUT
touch $SIG
chmod 777 $OUT
chmod 777 $SIG

#'By default,  without using this param,  generateData.pl will run as  '--enableDateDedupingWith NEWEST
sudo -u frsadmin $PROGRAM --start $SDAY --end $EDAY --output-file $OUT  --service $SERVICE --org $ORG #--query "$QUERY"

fi
```



-----------
##  Recommended Notes

- Bash Manual [reference](https://www.gnu.org/software/bash/manual/bash.html)
- The Bash home page [http://www.gnu.org/software/bash/](http://www.gnu.org/software/bash/).