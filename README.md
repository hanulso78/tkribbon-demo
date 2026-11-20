# tkribbon demo

Try **tkribbon**, an Office-style ribbon, docking panes and 60+ custom-drawn widgets for Tcl/Tk, written in C. It
runs on **Windows** and **Linux** (X11), in Tcl/Tk 8.6 and 9 and in Python's tkinter. This repository holds the demo
programs only; they need nothing installed, not even Tcl/Tk.

![tkribbon demo on Windows](screenshots/windows/demo-start.png)

## About this release

tkribbon is planned as a commercial product. Before deciding on licensing and pricing, I am releasing these demo
programs to see whether the library is useful to Tcl/Tk developers and what they would need from it. That is why the
programs are time-limited and the source is not public yet.

Your feedback helps decide what comes next: which widgets you would use, what is missing, which platforms or Tcl/Tk
versions matter to you, and what kind of license would work for you (per developer, per project, source included,
and so on). Please share it in the [Issues](https://github.com/hanulso78/tkribbon-demo/issues).

## Download

Get the files from the [Releases](https://github.com/hanulso78/tkribbon-demo/releases) page. Each platform has the
same two programs:

- **tkribbon-demo**: one window with a ribbon, docking panes, a code editor, widgets, a data grid with 20,000 rows,
  charts, a setup wizard, and every example in tabs.
- **tkribbon-examples**: the examples launcher, with 106 small programs, one per widget or topic, grouped by topic
  with a filter box. Double-click one to run it in its own window.

| Platform | File | Notes |
|---|---|---|
| Windows | `tkribbon-demo.exe`, `tkribbon-examples.exe` | Windows 10 or 11, 64-bit |
| Linux | `tkribbon-demo-linux-x86_64.tar.gz` | Both programs in one archive; x86-64 with glibc 2.28 or newer |
| Python | `tkribbon-0.1.0-py3-none-win_amd64.whl`, `tkribbon-0.1.0-py3-none-manylinux_2_28_x86_64.whl` | The library for tkinter, Python 3.8 or newer: `pip install <file>` |

All the files are time-limited: they work for **15 days** from the first start on a computer.

### Windows

- The programs are not signed, so Windows SmartScreen may ask before starting them ("More info", then "Run anyway").
- On the first start a program unpacks its files into `%LOCALAPPDATA%\tkribbon-demo` (or `tkribbon-examples`).
  To remove them, delete those folders.

### Linux

```sh
tar -xzf tkribbon-demo-linux-x86_64.tar.gz
cd tkribbon-demo-linux-x86_64
./tkribbon-demo
./tkribbon-examples
```

- Built and tested on AlmaLinux 8; it should run on any x86-64 distribution with glibc 2.28 or newer (RHEL/Rocky 8+,
  Fedora, Debian 10+, Ubuntu 20.04+, and so on). Each program holds its own Tcl/Tk 9, so only the usual desktop libraries are needed: X11, Xft, fontconfig
  and freetype.
- It runs on X11 desktops and on Wayland desktops through XWayland.
- On the first start a program unpacks its files into `~/.cache/tkribbon-demo` (or `tkribbon-examples`); the trial
  record is kept in `~/.config/tkribbon`. To remove them, delete those folders.

## What is in tkribbon

| Package | What it adds |
|---|---|
| `tkribbon` | Ribbon (tabs, groups, galleries, quick access toolbar, key tips, contextual tabs, backstage), drawn title bar and frameless windows, docking panes (tabify, split, float, auto-hide), dockable toolbars, menu bar and drawn menus, themes with DPI scaling, and widgets: buttons, line and masked edits, auto-completion, date and time edits, sliders, dials, ratings, color and font pickers, tree list, data grid, property grid, pivot table, spreadsheet, calendar scheduler, Gantt timeline, Kanban board, node editor, diagram editor, photo editor, hex editor, rich text editor, Markdown viewer, terminal, chat view, map view, QR codes and bar codes, web view (WebView2 on Windows), task, input and progress dialogs, notification area (tray) icons, drag and drop, JSON and XML, saving and restoring the window arrangement |
| `tkscintilla` | Scintilla code editor with ruler, minimap, find bar, diff view, code outline and autocomplete |
| `tkgraph` | Graphs and charts: lines, bars, pie, heatmap, polar, 3D surfaces, figures with several plots, export |
| `tkhtmlview` | HTML/CSS viewer: flex, grid, CSS variables, gradients, history, find, zoom, forms |

All commands live in the `rtk::` namespace and load through stubs in Tcl/Tk 8.5, 8.6 and 9:

```tcl
package require tkribbon

::rtk::theme darkgray
rtk::ribbon .r
.r tab add home -text Home
.r group add home g -text Greeting
.r item add g hello -text "Say hello" -command {puts "Hello, world!"}
pack .r -fill x
```

The same widgets are classes in Python:

```python
import tkinter as tk
import tkribbon as rtk

root = tk.Tk()
rtk.theme("darkgray")
ribbon = rtk.Ribbon(root)
ribbon.tab.add("home", text="Home")
ribbon.group.add("home", "greeting", text="Greeting")
ribbon.item.add("greeting", "hello", text="Say hello", command=lambda: print("Hello, world!"))
ribbon.pack(fill="x")
root.mainloop()
```

## Screenshots

The same demo on Windows 10 and on Linux (AlmaLinux 8, Tcl/Tk 9).

### Windows

**Code editor** (tkscintilla) with the ruler, minimap and margin tips

![Code editor on Windows](screenshots/windows/demo-editor.png)

**Dashboard example**: navigation view, tile dashboard, seven-segment clock, LEDs, ratings

![Dashboard on Windows](screenshots/windows/demo-dashboard.png)

**Graphs** (tkgraph): smooth lines with area fill, steps, zoom and crosshairs

![Graphs on Windows](screenshots/windows/demo-graph.png)

**Data grid** with 20,000 rows, grouping and filters

![Data grid on Windows](screenshots/windows/demo-data.png)

**Widgets** in the light theme

![Widgets in the light theme on Windows](screenshots/windows/demo-widgets-light.png)

**Examples launcher** (`tkribbon-examples.exe`)

![Examples launcher on Windows](screenshots/windows/examples.png)

### Linux

**Start page**

![Start page on Linux](screenshots/linux/demo-start.png)

**Code editor** (tkscintilla)

![Code editor on Linux](screenshots/linux/demo-editor.png)

**Dashboard example**

![Dashboard on Linux](screenshots/linux/demo-dashboard.png)

**Graphs** (tkgraph)

![Graphs on Linux](screenshots/linux/demo-graph.png)

**Data grid**

![Data grid on Linux](screenshots/linux/demo-data.png)

**Widgets** in the light theme

![Widgets in the light theme on Linux](screenshots/linux/demo-widgets-light.png)

**Examples launcher** (`tkribbon-examples`)

![Examples launcher on Linux](screenshots/linux/examples.png)

## Feedback

Questions, comments and bug reports are welcome in the [Issues](https://github.com/hanulso78/tkribbon-demo/issues).
