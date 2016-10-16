---
title: "WorkerArchetype::Initialize"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "reference"
f1_keywords: 
  - "Initialize"
  - "WorkerArchetype.Initialize"
  - "WorkerArchetype::Initialize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Initialize method"
ms.assetid: 5d82463f-dba9-461c-bc8d-692ff15ed17e
caps.latest.revision: 10
ms.author: "mblome"
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
# WorkerArchetype::Initialize
Called to initialize the worker object before any requests are passed to [Execute](../atl/workerarchetype--execute.md).  
  
## Syntax  
  
```  
  
      BOOL Initialize(  
   void* pvParam  
) throw( );  
```  
  
#### Parameters  
 `pvParam`  
 A custom parameter understood by the worker class. Also passed to [Terminate](../atl/workerarchetype--terminate.md) and [Execute](../atl/workerarchetype--execute.md).  
  
## Return Value  
 Return **TRUE** on success, **FALSE** on failure.  
  
## Requirements  
 **Header:** atlutil.h  
  
## See Also  
 [Worker Archetype](../atl/worker-archetype.md)