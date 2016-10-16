---
title: "Error Handling and Notification"
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
ms.assetid: b621cf60-d869-451a-b05e-dc86d78addaa
caps.latest.revision: 7
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
# Error Handling and Notification
For more information on error handling and notification, see [Understanding the Helper Function](assetId:///6279c12c-d908-4967-b0b3-cabfc3e91d3d).  
  
 For more information on hook functions, see [Structure and Constant Definitions](../VS_visualcpp/Structure-and-Constant-Definitions.md).  
  
 If your program uses delay-loaded DLLs, it must handle errors robustly since failures that occur while the program is running will result in unhandled exceptions. Failure handling is comprised of two portions:  
  
 Recovery through a hook.  
 If your code needs to recover or provide an alternate library and/or routine on failure, a hook can be provided to the helper function that can supply or remedy the situation. The hook routine needs to return a suitable value, so that processing can continue (an HINSTANCE or FARPROC) or 0 to indicate that an exception should be thrown. It could also throw its own exception or **longjmp** out of the hook. There are notification hooks and failure hooks.  
  
 Reporting via an exception.  
 If all that is necessary for handling the error is to abort the procedure, no hook is necessary as long as the user code can handle the exception.  
  
 The following topics discuss error handling and notification:  
  
-   [Notification Hooks](../VS_visualcpp/Notification-Hooks.md)  
  
-   [Failure Hooks](../VS_visualcpp/Failure-Hooks.md)  
  
-   [Exceptions](../VS_visualcpp/Exceptions--C-C---.md)  
  
## See Also  
 [Linker Support for Delay-Loaded DLLs](../VS_visualcpp/Linker-Support-for-Delay-Loaded-DLLs.md)