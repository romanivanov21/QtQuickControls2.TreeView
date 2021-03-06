# QtQuickControls2.TreeView
[![Build Status](https://travis-ci.org/ColinDuquesnoy/QtQuickControls2.TreeView.svg?branch=master)](https://travis-ci.org/ColinDuquesnoy/QtQuickControls2.TreeView)

This repository contains the sources for a QtQuickControls2 based TreeView control that you can use in your qml desktop application.

## State

This user control is in alpha version. There are some missing features or things that do not work yet:

- dynamic insertion works by appending items, order is not correct at the moment
- dynamic removal does not work
- there is no selection model
- root index cannot be set

## Why this project?

QtQuickControls2 do not provide a TreeView control yet because they focus on mobile application development where 
tree view are not that common. But QtQuickControls2 can also be used to develop nice desktop applications and a tree view
component is often needed. I needed a TreeView for one of my personal (but still private) project so I decided to 
create a one myself.

## Solution

The solution I found is to use a ListView Item as the base qml item of the tree view and use a proxy model that 
flatten a source tree model. 

## Source code organisation

* The core of the library can be found in the ``lib`` folder. This is a header only library that contains the ``TreeViewModel`` 
and the ``TreeItemViewModel``

* The ``imports`` directory contains the qml implementation of the TreeView and the TreeItemView. 
The TreeItemView delegate is extensible: you can specify the component to use to to render both the arrow and the display items. 
It handles indentation and expanding/collapsing of nodes automatically for you.

* There is also a small ``tests`` suite (using the [catch testing framework](https://github.com/philsquared/Catch) ) that you can run using ``ctest``.

* The ``example`` create two tree model: a ``StandardItemModel`` and ``QFileSystemModel``. It then wraps those two models in a 
``TreeViewModel``  and exposes them via a context property.


## How can I use it ?

License here is "super-open", not even copy-left or copy-right, just use it as you want, as it's the most practical to you:

- if you want to use it as GIT submodule and compile it in your app, do it!
- if you prefer separate project as a shared library, do it!
- if you need to modify the project to be able to integrate in you app (opensource or not), do it!
- if you want to share your work on the library, thanks a lot, but if you don't, no problem!

