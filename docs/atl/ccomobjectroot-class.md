---
title: "CComObjectRoot Class"
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
  - "CComObjectRoot"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CComObjectRoot class"
ms.assetid: f8797c38-6e73-4f67-85c2-71654cffa8eb
caps.latest.revision: 12
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
# CComObjectRoot Class
This typedef of [CComObjectRootEx](../atl/ccomobjectrootex-class.md) is templatized on the default threading model of the server.  
  
## Syntax  
  
```
typedef CComObjectRootEx<CComObjectThreadModel> CComObjectRoot;
```  
  
## Remarks  
 `CComObjectRoot` is a `typedef` of [CComObjectRootEx](../atl/ccomobjectrootex-class.md) templatized on the default threading model of the server. Thus [CComObjectThreadModel](../Topic/CComObjectThreadModel.md) will reference either [CComSingleThreadModel](../atl/ccomsinglethreadmodel-class.md) or [CComMultiThreadModel](../atl/ccommultithreadmodel-class.md).  
  
 `CComObjectRootEx` handles object reference count management for both nonaggregated and aggregated objects. It holds the object reference count if your object is not being aggregated, and holds the pointer to the outer unknown if your object is being aggregated. For aggregated objects, `CComObjectRootEx` methods can be used to handle the failure of the inner object to construct, and to protect the outer object from deletion when inner interfaces are released or the inner object is deleted.  
  
## Requirements  
 **Header:** atlcom.h  
  
## See Also  
 [CComObjectRootEx Class Members](assetId:///e3ce9c3d-9c8e-4fe5-b682-8e56740a0164)   
 [CComObjectRootEx Class](../atl/ccomobjectrootex-class.md)   
 [CComAggObject Class](../atl/ccomaggobject-class.md)   
 [CComObject Class](../atl/ccomobject-class.md)   
 [CComPolyObject Class](../atl/ccompolyobject-class.md)   
 [Class Overview](../atl/atl-class-overview.md)
