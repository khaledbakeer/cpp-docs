---
title: "multimap::generic_value (STL-CLR)"
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
  - "cliext::multimap::generic_value"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "generic_value member [STL/CLR]"
ms.assetid: e403233f-5132-45ca-be04-2c85e923f37d
caps.latest.revision: 6
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
# multimap::generic_value (STL/CLR)
The type of an element for use with the generic interface for the container.  
  
## Syntax  
  
```  
typedef GValue generic_value;  
```  
  
## Remarks  
 The type describes an object of type `GValue` that describes the stored element value for use with the generic interface for this template container class.  
  
## Example  
  
```  
// cliext_multimap_generic_value.cpp   
// compile with: /clr   
#include <cliext/map>   
  
typedef cliext::multimap<wchar_t, int> Mymultimap;   
int main()   
    {   
    Mymultimap c1;   
    c1.insert(Mymultimap::make_value(L'a', 1));   
    c1.insert(Mymultimap::make_value(L'b', 2));   
    c1.insert(Mymultimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Mymultimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// construct a generic container   
    Mymultimap::generic_container^ gc1 = %c1;   
    for each (Mymultimap::value_type elem in gc1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
// get an element and display it   
    Mymultimap::generic_iterator gcit = gc1->begin();   
    Mymultimap::generic_value gcval = *gcit;   
    System::Console::WriteLine(" [{0} {1}]", gcval->first, gcval->second);   
    return (0);   
    }  
  
```  
  
  **[a 1] [b 2] [c 3]**  
 **[a 1] [b 2] [c 3]**  
 **[a 1]**   
## Requirements  
 **Header:** \<cliext/map>  
  
 **Namespace:** cliext  
  
## See Also  
 [multimap (STL/CLR)](../cli/multimap--stl-clr-.md)   
 [multimap::generic_container (STL/CLR)](../cli/multimap--generic_container--stl-clr-.md)   
 [multimap::generic_iterator (STL/CLR)](../cli/multimap--generic_iterator--stl-clr-.md)   
 [multimap::generic_reverse_iterator (STL/CLR)](../cli/multimap--generic_reverse_iterator--stl-clr-.md)