# STATIC BRANCH PRED

ajouter à gem5/src/cpu/pred/BranchPredictor.py :

```
class StaticTakenBP(BranchPredictor):
    type = "StaticTakenBP"
    cxx_class = "gem5::branch_prediction::StaticTakenBP"
    cxx_header = "cpu/pred/static_bp.hh"

class StaticNotTakenBP(BranchPredictor):
    type = "StaticNotTakenBP"
    cxx_class = "gem5::branch_prediction::StaticNotTakenBP"
    cxx_header = "cpu/pred/static_bp.hh"
```

ajouter à gem5/src/cpu/pred/SConscript dans SimObject :


```
'StaticTakenBP', 'StaticNotTakenBP'
```

ajouter à gem5/src/cpu/pred/SConscript :

```
Source('static_bp.cc')
```

enfin rebuilder gem5 dans gem5

```
scons build/RISCV/gem5.opt -j 8
```