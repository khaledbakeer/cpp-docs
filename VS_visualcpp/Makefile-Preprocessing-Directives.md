---
title: "Makefile Preprocessing Directives"
ms.custom: na
ms.date: 10/03/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bcedeccb-d981-469d-b9e8-ab5d097fd8c2
caps.latest.revision: 8
manager: ghogen
translation.priority.ht: 
  - cs-cz
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pl-pl
  - pt-br
  - ru-ru
  - tr-tr
  - zh-cn
  - zh-tw
---
# Makefile Preprocessing Directives
Preprocessing directives are not case sensitive. The initial exclamation point (!) must appear at the beginning of the line. Zero or more spaces or tabs can appear after the exclamation point, for indentation.  
  
 **!CMDSWITCHES**  
 {**+**&#124; **–**}*option*... Turns each *option* listed on or off. Spaces or tabs must appear before the + or – operator; none can appear between the operator and the [option letters](../VS_visualcpp/NMAKE-Options.md). Letters are not case sensitive and are specified without a slash ( / ). To turn some options on and others off, use separate specifications of **!CMDSWITCHES**.  
  
 Only /D, /I, /N, and /S can be used in a makefile. In Tools.ini, all options are allowed except /F, /HELP, /NOLOGO, /X, and /?. Changes specified in a description block do not take effect until the next description block. This directive updates **MAKEFLAGS**; changes are inherited during recursion if **MAKEFLAGS** is specified.  
  
 **!ERROR**  *text*  
 Displays *text* in error U1050, then halts NMAKE, even if /K, /I, **.IGNORE**, **!CMDSWITCHES**, or the dash (–) command modifier is used. Spaces or tabs before *text* are ignored.  
  
 **!MESSAGE**  *text*  
 Displays *text* to standard output. Spaces or tabs before *text* are ignored.  
  
 **!INCLUDE**[ **<**] *filename*[ **>**]  
 Reads *filename* as a makefile, then continues with the current makefile. NMAKE searches for *filename* first in the specified or current directory, then recursively through directories of any parent makefiles, then, if *filename* is enclosed by angle brackets (< >), in directories specified by the **INCLUDE** macro, which is initially set to the INCLUDE environment variable. Useful to pass **.SUFFIXES** settings, **.PRECIOUS**, and inference rules to recursive makefiles.  
  
 **!IF**  `constantexpression`  
 Processes statements between **!IF** and the next **!ELSE** or `!ENDIF` if `constantexpression` evaluates to a nonzero value.  
  
 **!IFDEF**  *macroname*  
 Processes statements between `!IFDEF` and the next **!ELSE** or `!ENDIF` if *macroname* is defined. A null macro is considered to be defined.  
  
 **!IFNDEF**  *macroname*  
 Processes statements between **!IFNDEF** and the next **!ELSE** or `!ENDIF` if *macroname* is not defined.  
  
 **!ELSE**[**IF** *constantexpression* &#124; **IFDEF** *macroname*&#124; **IFNDEF** *macroname*]  
 Processes statements between **!ELSE** and the next `!ENDIF` if the prior **!IF**, `!IFDEF`, or **!IFNDEF** statement evaluated to zero. The optional keywords give further control of preprocessing.  
  
 **!ELSEIF**  
 Synonym for **!ELSE IF**.  
  
 **!ELSEIFDEF**  
 Synonym for **!ELSE IFDEF**.  
  
 **!ELSEIFNDEF**  
 Synonym for **!ELSE IFNDEF**.  
  
 `!ENDIF`  
 Marks the end of an **!IF**, `!IFDEF`, or **!IFNDEF** block. Any text after `!ENDIF` on the same line is ignored.  
  
 **!UNDEF**  *macroname*  
 Undefines *macroname*.  
  
## See Also  
 [Makefile Preprocessing](../VS_visualcpp/Makefile-Preprocessing.md)