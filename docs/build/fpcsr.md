---
title: "FpCsr"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: dff95d5d-7589-4432-82db-64b459c24352
caps.latest.revision: 5
ms.author: "corob"
manager: "ghogen"
translation.priority.ht: 
  - "cs-cz"
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pl-pl"
  - "pt-br"
  - "ru-ru"
  - "tr-tr"
  - "zh-cn"
  - "zh-tw"
---
# FpCsr
The register state also includes the x87 FPU control word. The calling convention dictates this register to be nonvolatile.  
  
 The x87 FPU control word register is set to the following standard values at the start of program execution:  
  
```  
FPCSR[0:6]: Exception masks all 1's (all exceptions masked)  
FPCSR[7]: Reserved – 0  
FPCSR[8:9]: Precision Control – 10B (double precision)  
FPCSR[10:11]: Rounding  control - 0 (round to nearest)  
FPCSR[12]: Infinity control – 0 (not used)  
```  
  
 A callee that modifies any of the fields within FPCSR must restore them before returning to its caller. Furthermore, a caller that has modified any of these fields must restore them to their standard values before invoking a callee unless by agreement the callee expects the modified values.  
  
 There are two exceptions to the rules regarding the non-volatility of the control flags:  
  
1.  In functions where the documented purpose of the given function is to modify the nonvolatile FpCsr flags.  
  
2.  When it is provably correct that the violation of these rules results in a programs that behaves/means the same as a program where these rules are not violated, for example, through whole-program analysis.  
  
## See Also  
 [Calling Convention](../build/calling-convention.md)