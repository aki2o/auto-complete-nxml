What's this?
============

This is a extension of Emacs provides completion by auto-complete.el on nXML-mode.


Feature
=======

### Start completion automatically

On nXML-mode, completion is started when you keystroke the bound key for starting completion defalut "C-RET".  
I think this action is good when completion use default interface of Emacs.  
But the interface of auto-complete.el is lighter than it.  
So, start completion automatically according to the context as much as possible.

When you are on nXML-mode, keystroke "<". Then ...

![Demo1](image/demo1.png)

Subsequently, if you select "table" ...

![Demo2](image/demo2.png)

Subsequently, if you select "style" ...

![Demo3](image/demo3.png)

Subsequently, if you select "font-size" ...

![Demo4](image/demo4.png)

### CSS property and its value are available as the candidate

nXML-mode can't complete CSS property and its value.  
But their definition are in auto-complete.el.  
So, CSS property and its value are available when completion of attribute value.  
See above screenshot.

### Do completion when you are on the content of the element.

nXML-mode can't complete on the content of the element.  
But their definition exists in the used schema of RELAX NG and XML Schema.  
So, when you are on the content of the element, do completion using them.  
If it is not selective, do completion using the words in the nXML-mode buffers that you opened.

![Demo5](image/demo_content.png)

### Completion of word using anything-project.el

When you are in not selective content of the element, can use only the words in the opened buffer.  
But it is too much trouble.  
So, if anything-project.el is available, do completion using the words in the project files of anything-project.el.

### Complete available "xmlns" attribute automatically

nXML-mode can manage the namespace of the used schema.  
For example, if you wrote the following,  

```html
<html xmlns="http://www.w3.org/TR/xhtml1"
      xmlns:math="http://www.w3.org/1998/Math/MathML">
```

the defined in "http://www.w3.org/TR/xhtml1" are displayed without prefix,  
the defined in "http://www.w3.org/1998/Math/MathML" are displayed with "math:".  

But when complete "xmlns" attribute,   
nXML-mode don't complete namespace other than the default even if they exists in used schema.  
In this case, you have to know which available namespace is.  
Then, it is too much trouble.  
So, when complete default namespace, complete all available namespaces automatically.

![Demo6](image/demo_xmlns1.png)

If you select "xmlns" ...

![Demo7](image/demo_xmlns2.png)

### Popup help of element and attribute

When complete element and attribute, popup help about them beside displayed candidates.  
And when you keystroke the bound key for popup help, popup help about pointed.  
Abount binding the key for popup help, see Configuration section below.

### Toggle on/off automatic completion

In default, completion is started automatically.  
But, you can disable it temporarily or constantly by the following way.  

* For disable constantly, eval `(setq auto-complete-nxml-automatic-p nil)`
* For disable/enable while editing, M-x `auto-complete-nxml-toggle-automatic`

About keybind of `auto-complete-nxml-toggle-automatic`, see Configuration section below.


Install
=======

You can install by the following way.

### By package.el

2013/09/15 It's available by using melpa.  

### By el-get.el

2013/04/18 It's available. But, master branch only.  

### By auto-install.el

```lisp
(auto-install-from-url "https://raw.github.com/aki2o/auto-complete-nxml/master/auto-complete-nxml.el")
```

### Otherwise

download "auto-complete-nxml.el" manually and put it in your load-path.


Configuration
=============

```lisp
(require 'auto-complete-nxml)

;; Keystroke for popup help about something at point.
(setq auto-complete-nxml-popup-help-key "C-:")

;; Keystroke for toggle on/off automatic completion.
(setq auto-complete-nxml-toggle-automatic-key "C-c C-t")

;; If you want to start completion manually from the beginning
(setq auto-complete-nxml-automatic-p nil)
```


Tested On
=========

* Emacs ... GNU Emacs 23.3.1 (i386-mingw-nt5.1.2600) of 2011-08-15 on GNUPACK
* auto-complete.el ... Version 1.4


**Enjoy!!!**

