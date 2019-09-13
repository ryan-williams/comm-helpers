# comm-helpers
Wrappers and aliases for the bash `comm` utility for comparing lines between two inputs

## Install
```bash
git clone git@github.com:ryan-williams/comm-helpers.git
echo "source $PWD/comm-helpers/.comm-rc" >> ~/.bashrc
. ~/.bashrc
```

## Usage

### `c1`, `c2`, `c3`, `c12`, `c13`, `c23`
Invert the `-1`, `-2`, and `-3` flags to `comm`, which normally *exclude* columns, for a more concise and intuitive API:

### `comm-count` (`cmc`), `comm-sort` (`cms`), `comm-count-sort` (`cmcs`)
Wrap `comm`, optionally [sort the inputs] and [count the output lines in each selected category (left only, right only, both)].

Count multiples of 2 (but not 3), 3 (but not 2), and 6 (2 and 3), in (0,60]:
```bash
cmcs <(seq 60 -2 2) <(seq 3 3 60)
#       20	      10	      10
```
Note: the multiples of 2 (`seq 60 -2 2`) are input in descending order, but `cmcs` sorts the inputs before "joining" them.

Sort and show the multiples of 2, 3, and 6 in (0,30]:
```bash
cms <(seq 30 -2 2) <(seq 3 3 30) | sort -n
# 2
# 	3
# 4
# 		6
# 8
# 	9
# 10
# 		12
# 14
# 	15
# 16
# 		18
# 20
# 	21
# 22
# 		24
# 26
# 	27
# 28
# 		30
```
