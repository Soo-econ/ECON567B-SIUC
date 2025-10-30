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
> For simplicity, I usually name each frame the same as its dataset, but you can choose any name you prefer.

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
> **NOTE:** If you want to create frames and load datasets without switching to each frame immediately, you can use the following syntax:
```
frame create wagepan
frame wagepan: use wagepan, clear
frame create lowbirth
frame lowbirth: use lowbirth, clear
```
This will load each dataset into its own frame.

You can later switch to any frame you need using the cwf command:
```
cwf first 
```
This makes it incredibly convenient to manage and work with several datasets simultaneously!

### 1.1 `frlink` : Linking Frames (similar to `merge`)
The `frlink` command serves a similar role to the `merge` command in Stata.

It allows you to link **datasets across frames** based on a coomon identifier.

**Step 1.** Link two frames using a common variable (usually an ID)
```
frlink m:1 id, frame(wagepan)
```

**Step 2.** Bring variables from the linked frame.

Once linked (Given that our currunt working frame is lowbirth), you can retrieve variables from *wagepan* frame.

To bring all variables *(*)* except year, use: 
```
frget *, from(wagepan) exclude(year)
```
If you only need specific variables, list them explicitly:
```
frget hours bus, from(wagepan)
```
In this way, you can easily **create frames, load datasets, and link them**, making your workflow more flexible and efficient!


