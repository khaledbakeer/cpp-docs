---
title: "ostrstream Class"
ms.custom: na
ms.date: "10/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: na
ms.suite: na
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: na
ms.topic: "article"
f1_keywords: 
  - "std.oststream"
  - "oststream"
  - "std::oststream"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ostrstream class"
ms.assetid: e2e34679-b266-4728-a8e1-8eda5d400e46
caps.latest.revision: 19
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
# ostrstream Class
Describes an object that controls insertion of elements and encoded objects into a stream buffer of class [strstreambuf](../stdcpplib/strstreambuf-class.md).  
  
## Syntax  
  
```
class ostrstream : public ostream
```  
  
## Remarks  
 The object stores an object of class `strstreambuf`.  
  
> [!NOTE]
>  This class is deprecated. Consider using [ostringstream](../stdcpplib/-sstream--typedefs.md#ostringstream) or [wostringstream](../stdcpplib/-sstream--typedefs.md#wostringstream) instead.  
  
### Constructors  
  
|||  
|-|-|  
|[ostrstream](#ostrstream__ostrstream)|Constructs an object of type `ostrstream`.|  
  
### Member Functions  
  
|||  
|-|-|  
|[freeze](#ostrstream__freeze)|Causes a stream buffer to be unavailable through stream buffer operations.|  
|[pcount](#ostrstream__pcount)|Returns a count of the number of elements written to the controlled sequence.|  
|[rdbuf](#ostrstream__rdbuf)|Returns a pointer to the stream's associated `strstreambuf` object.|  
|[str](#ostrstream__str)|Calls [freeze](../stdcpplib/strstreambuf-class.md#strstreambuf__freeze), and then returns a pointer to the beginning of the controlled sequence.|  
  
## Requirements  
 **Header:** \<strstream>  
  
 **Namespace:** std  
  
##  <a name="ostrstream__freeze"></a>  ostrstream::freeze  
 Causes a stream buffer to be unavailable through stream buffer operations.  
  
```
void freeze(bool  _Freezeit = true);
```  
  
### Parameters  
 `_Freezeit`  
 A `bool` indicating whether you want the stream to be frozen.  
  
### Remarks  
 The member function calls [rdbuf](#ostrstream__rdbuf) -> [freeze](../stdcpplib/strstreambuf-class.md#strstreambuf__freeze)(_ *Freezeit*).  
  
### Example  
  See [strstream::freeze](../stdcpplib/strstreambuf-class.md#strstreambuf__freeze) for an example that uses **freeze**.  
  
##  <a name="ostrstream__ostrstream"></a>  ostrstream::ostrstream  
 Constructs an object of type `ostrstream`.  
  
```
ostrstream();

ostrstream(char* ptr,
    streamsize  count,
    ios_base::openmode  _Mode = ios_base::out);
```  
  
### Parameters  
 `ptr`  
 The buffer.  
  
 `count`  
 The size of the buffer in bytes.  
  
 `_Mode`  
 The input and output mode of the buffer. See [ios_base::openmode](../stdcpplib/ios_base-class.md#ios_base__openmode) for more information.  
  
### Remarks  
 Both constructors initialize the base class by calling [ostream](../stdcpplib/-ostream--typedefs.md#ostream)( **sb**), where **sb** is the stored object of class [strstreambuf](../stdcpplib/strstreambuf-class.md). The first constructor also initializes **sb** by calling `strstreambuf`. The second constructor initializes the base class one of two ways:  
  
-   If `_Mode` & **ios_base::app**== 0, then `ptr` must designate the first element of an array of `count` elements, and the constructor calls `strstreambuf`( `ptr`, `count`, `ptr`).  
  
-   Otherwise, `ptr` must designate the first element of an array of count elements that contains a C string whose first element is designated by `ptr`, and the constructor calls `strstreambuf`( `ptr`, `count`, `ptr` + `strlen`( `ptr`) ).  
  
##  <a name="ostrstream__pcount"></a>  ostrstream::pcount  
 Returns a count of the number of elements written to the controlled sequence.  
  
```
streamsize pcount() const;
```  
  
### Return Value  
 The number of elements written to the controlled sequence.  
  
### Remarks  
 The member function returns [rdbuf](#ostrstream__rdbuf) -> [pcount](../stdcpplib/strstreambuf-class.md#strstreambuf__pcount).  
  
### Example  
  See [strstream::pcount](../stdcpplib/strstreambuf-class.md#strstreambuf__pcount) for a sample that uses `pcount`.  
  
##  <a name="ostrstream__rdbuf"></a>  ostrstream::rdbuf  
 Returns a pointer to the stream's associated strstreambuf object.  
  
```
strstreambuf *rdbuf() const
```  
  
### Return Value  
 A pointer to the stream's associated strstreambuf object.  
  
### Remarks  
 The member function returns the address of the stored stream buffer of type **pointer** to [strstreambuf](../stdcpplib/strstreambuf-class.md).  
  
### Example  
  See [strstreambuf::pcount](../stdcpplib/strstreambuf-class.md#strstreambuf__pcount) for a sample that uses `rdbuf`.  
  
##  <a name="ostrstream__str"></a>  ostrstream::str  
 Calls [freeze](../stdcpplib/strstreambuf-class.md#strstreambuf__freeze), and then returns a pointer to the beginning of the controlled sequence.  
  
```
char *str();
```  
  
### Return Value  
 A pointer to the beginning of the controlled sequence.  
  
### Remarks  
 The member function returns [rdbuf](#ostrstream__rdbuf) -> [str](../stdcpplib/strstreambuf-class.md#strstreambuf__str).  
  
### Example  
  See [strstream::str](../stdcpplib/strstreambuf-class.md#strstreambuf__str) for a sample that uses **str**.  
  
## See Also  
 [ostream](../stdcpplib/-ostream--typedefs.md#ostream)   
 [Thread Safety in the C++ Standard Library](../stdcpplib/thread-safety-in-the-c---standard-library.md)   
 [iostream Programming](../stdcpplib/iostream-programming.md)   
 [iostreams Conventions](../stdcpplib/iostreams-conventions.md)
