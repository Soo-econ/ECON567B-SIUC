# Stata Session I

Hi everyone,
I am sharing some of the basic Stata syntax we covered in class!




## Contents
- [frame](#frame-section)


## 1. Using `frame` to Manage Multiple Datasets <a id="frame-section"></a>

Stata's `frame` command allows you to keep and manage **multiple datasets** in memory at once.
This is useful because you can work with several datasets simultaneously without having to save and reload them repeatedly.

**Step 1. Clear all Frames**

Before starting, it's a good idea to clear all exsiting frames:
```
frames reset
```
**Step 2. Create New Frames**

Let's create two empty frames named *wagepan* and *lowbirth*:
```
frame create wagepan
frame create lowbirth
```
**Step 3. Change the Current working Frame**

Now, switch the current working frame to wagepan, first,
```
frame change wagepan
```
> Alternatively, you can use `cwf` (short for current working frame):
```
cwf wagepan
```
**Step 4. Load a Dataset into the Current Frame**

load a dataset into your current working frame (wagepan):
```
use wagepan, clear
```
**Step 4. Switch to Another Frame**

Next, switch to lowbirth frame and load another dataset
```
cwf lowbirth
use lowbirth, clear
```


