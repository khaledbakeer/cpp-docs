---
title: "hash_multimap::find (STL-CLR)"
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
  - "cliext::hash_multimap::find"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "find member [STL/CLR]"
ms.assetid: ce839c5e-b8c5-434e-9cc0-e4c6ee6a6bb3
caps.latest.revision: 13
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
# hash_multimap::find (STL/CLR)
Finds an element that matches a specified key.  
  
## Syntax  
  
```  
iterator find(key_type key);  
```  
  
#### Parameters  
 key  
 Key value to search for.  
  
## Remarks  
 If at least one element in the controlled sequence has equivalent ordering with `key`, the member function returns an iterator designating one of those elements; otherwise it returns [hash_multimap::end (STL/CLR)](../cli/hash_multimap--end--stl-clr-.md)`()`. You use it to locate an element currently in the controlled sequence that matches a specified key.  
  
## Example  
  
```  
// cliext_hash_multimap_find.cpp   
// compile with: /clr   
#include <cliext/hash_map>   
  
typedef cliext::hash_multimap<wchar_t, int> Myhash_multimap;   
int main()   
    {   
    Myhash_multimap c1;   
    c1.insert(Myhash_multimap::make_value(L'a', 1));   
    c1.insert(Myhash_multimap::make_value(L'b', 2));   
    c1.insert(Myhash_multimap::make_value(L'c', 3));   
  
// display contents " [a 1] [b 2] [c 3]"   
    for each (Myhash_multimap::value_type elem in c1)   
        System::Console::Write(" [{0} {1}]", elem->first, elem->second);   
    System::Console::WriteLine();   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'A', c1.find(L'A') != c1.end());   
  
    Myhash_multimap::iterator it = c1.find(L'b');   
    System::Console::WriteLine("find {0} = [{1} {2}]",   
        L'b', it->first, it->second);   
  
    System::Console::WriteLine("find {0} = {1}",   
        L'C', c1.find(L'C') != c1.end());   
    return (0);   
    }  
  
```  
  
  **[a 1] [b 2] [c 3]**  
**find A = False**  
**find b = [b 2]**  
**find C = False**   
## Description  
 Note that `find` does not guarantee which of several element it finds.  
  
## Requirements  
 **Header:** \<cliext/hash_map>  
  
 **Namespace:** cliext  
  
## See Also  
 [hash_multimap (STL/CLR)](../cli/hash_multimap--stl-clr-.md)   
 [hash_multimap::equal_range (STL/CLR)](../cli/hash_multimap--equal_range--stl-clr-.md)   
 [hash_multimap::lower_bound (STL/CLR)](../cli/hash_multimap--lower_bound--stl-clr-.md)   
 [hash_multimap::upper_bound (STL/CLR)](../cli/hash_multimap--upper_bound--stl-clr-.md)