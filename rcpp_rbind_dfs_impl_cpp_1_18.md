# rcpp_rbind_dfs_impl.cpp:1:18: fatal error: Rcpp.h: No such file or directory

## Cause

Install a package that relies on Rcpp and uses it incorrectly:

```
devtools::install_github("richelbilderbeek/ribir")
```

(note that this package has been fixed now)

## Result

```
Downloading GitHub repo richelbilderbeek/ribir@master
from URL https://api.github.com/repos/richelbilderbeek/ribir/zipball/master
Installing ribir
'/usr/lib/R/bin/R' --no-site-file --no-environ --no-save --no-restore --quiet CMD  \
  INSTALL '/tmp/RtmpFCyuEU/devtools2fc9138d20da/richelbilderbeek-ribir-7283834'  \
  --library='/home/richel/R/i686-pc-linux-gnu-library/3.2' --install-tests 

* installing *source* package ‘ribir’ ...
** libs
g++ -I/usr/share/R/include -DNDEBUG      -fpic  -g -O2 -fstack-protector-strong -Wformat -Werror=format-security -Wdate-time -D_FORTIFY_SOURCE=2 -g  -c rcpp_rbind_dfs_impl.cpp -o rcpp_rbind_dfs_impl.o
rcpp_rbind_dfs_impl.cpp:1:18: fatal error: Rcpp.h: No such file or directory
compilation terminated.
/usr/lib/R/etc/Makeconf:143: recipe for target 'rcpp_rbind_dfs_impl.o' failed
make: *** [rcpp_rbind_dfs_impl.o] Error 1
ERROR: compilation failed for package ‘ribir’
* removing ‘/home/richel/R/i686-pc-linux-gnu-library/3.2/ribir’
Error: Command failed (1)
```

## Solution

The function `rcpp_rbind_dfs_impl` in the file `rcpp_rbind_dfs_impl.cpp` was incorrectly implemented.

## Not solutions

From [Romain Francois](http://stackoverflow.com/a/16260937), add to DESCRIPTION:

```
LinkingTo: Rcpp
```

Nor

```
sudo apt-get install r-base-dev
```

Nor

```
sudo apt-get install r-cran-rcpp
```