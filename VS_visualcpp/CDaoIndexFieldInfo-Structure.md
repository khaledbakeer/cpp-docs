---
title: "CDaoIndexFieldInfo Structure"
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
ms.assetid: 097ee8a6-83b1-4db7-8f05-d62a2deefe19
caps.latest.revision: 9
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
# CDaoIndexFieldInfo Structure
The `CDaoIndexFieldInfo` structure contains information about an index field object defined for data access objects (DAO).  
  
## Syntax  
  
```  
  
      struct CDaoIndexFieldInfo  
{  
   CString m_strName;          // Primary  
   BOOL m_bDescending;         // Primary  
};  
```  
  
#### Parameters  
 `m_strName`  
 Uniquely names the index field object. For details, see the topic "Name Property" in DAO Help.  
  
 *m_bDescending*  
 Indicates the index ordering defined by the index object. **TRUE** if the order is descending.  
  
## Remarks  
 An index object can have a number of fields, indicating which fields a tabledef (or a recordset based on a table) is indexed on. The references to Primary above indicate how the information is returned in the `m_pFieldInfos` member of a [CDaoIndexInfo](../VS_visualcpp/CDaoIndexInfo-Structure.md) object obtained by calling the `GetIndexInfo` member function of class [CDaoTableDef](../Topic/CDaoTableDef::GetIndexInfo.md) or [CDaoRecordset](../Topic/CDaoRecordset::GetIndexInfo.md).  
  
 Index objects and index field objects are not represented by an MFC class. Instead, the DAO objects underlying MFC objects of class [CDaoTableDef](../VS_visualcpp/CDaoTableDef-Class.md) or [CDaoRecordset](../VS_visualcpp/CDaoRecordset-Class.md) contain a collection of index objects, called the Indexes collection. Each index object, in turn, contains a collection of field objects. These classes supply member functions to access individual items of index information, or you can access them all at once with a `CDaoIndexInfo` object by calling the `GetIndexInfo` member function of the containing object. The `CDaoIndexInfo` object, then, has a data member, `m_pFieldInfos`, that points to an array of `CDaoIndexFieldInfo` objects.  
  
 Call the `GetIndexInfo` member function of the containing tabledef or recordset object in whose Indexes collection is stored the index object you are interested in. Then access the `m_pFieldInfos` member of the [CDaoIndexInfo](../VS_visualcpp/CDaoIndexInfo-Structure.md) object. The length of the `m_pFieldInfos` array is stored in `m_nFields`. `CDaoIndexFieldInfo` also defines a `Dump` member function in debug builds. You can use `Dump` to dump the contents of a `CDaoIndexFieldInfo` object.  
  
## Requirements  
 **Header:** afxdao.h  
  
## See Also  
 [Structures, Styles, Callbacks, and Message Maps](../VS_visualcpp/Structures--Styles--Callbacks--and-Message-Maps.md)   
 [CDaoTableDef::GetIndexInfo](../Topic/CDaoTableDef::GetIndexInfo.md)   
 [CDaoRecordset::GetIndexInfo](../Topic/CDaoRecordset::GetIndexInfo.md)