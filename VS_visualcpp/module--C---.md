---
title: "module (C++)"
ms.custom: na
ms.date: 10/05/2016
ms.devlang: 
  - C++
ms.prod: visual-studio-dev14
ms.reviewer: na
ms.suite: na
ms.technology: 
  - devlang-cpp
ms.tgt_pltfrm: na
ms.topic: language-reference
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
caps.latest.revision: 10
manager: ghogen
translation.priority.ht: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - ru-ru
  - zh-cn
  - zh-tw
translation.priority.mt: 
  - cs-cz
  - pl-pl
  - pt-br
  - tr-tr
---
# module (C++)
Defines the library block in the .idl file.  
  
## Syntax  
  
```  
  
      [ module (  
   type=dll,  
   name=string,  
   version=1.0,  
   uuid=uuid,  
   lcid=integer,  
   control=boolean,  
   helpstring=string,  
   helpstringdll=string,  
   helpfile=string,  
   helpcontext=integer,  
   helpstringcontext=integer,  
   hidden=boolean,  
   restricted=boolean,  
   custom=string,  
   resource_name=string,  
) ];  
```  
  
#### Parameters  
 ***type***  (optional)  
 Can be one of the following:  
  
-   **dll** Adds functions and classes that allow the resulting DLL to function as a in-process COM server. This is the default value.  
  
-   **exe** Adds functions and classes that allow the resulting executable to function as a out of process COM server.  
  
-   **service** Adds functions and classes that allow the resulting executable to function as an NT service.  
  
-   **unspecified** Disables injection of ATL code related to the module attribute: the injection of ATL Module class, global instance _AtlModule and entry point functions.  Does not disable injection of ATL code due to other attributes in the project.  
  
 ***name***  (optional)  
 The name of the library block.  
  
 ***version***  (optional)  
 The version number you want to assign to the library block. The default value is 1.0.  
  
 `uuid`  
 The unique ID for the library. If you omit this parameter, an ID will be automatically generated for the library. You may need to retrieve the *uuid* of your library block, which you can do by using the identifier **__uuidof(***libraryname***)**.  
  
 **lcid**  
 The localization parameter. See [lcid](http://msdn.microsoft.com/library/windows/desktop/aa367067) for more information.  
  
 **control** (optional)  
 Specifies that all coclasses in the library are controls.  
  
 **helpstring**  
 Specifies the type library.  
  
 ***helpstringdll***  (optional)  
 Sets the name of the .dll file to use to perform a document string lookup. See [helpstringdll](http://msdn.microsoft.com/library/windows/desktop/aa366860) for more information.  
  
 **helpfile** (optional)  
 The name of the Help file for the type library.  
  
 **helpcontext** (optional)  
 The Help ID for this type library.  
  
 **helpstringcontext** (optional)  
 See [helpstringcontext](../VS_visualcpp/helpstringcontext.md) for more information.  
  
 **hidden** (optional)  
 Prevents the entire library from being displayed. This usage is intended for use with controls. Hosts need to create a new type library that wraps the control with extended properties. See the [hidden](http://msdn.microsoft.com/library/windows/desktop/aa366861) MIDL attribute for more information.  
  
 **restricted** (optional)  
 Members of the library cannot be called arbitrarily. See the [restricted](http://msdn.microsoft.com/library/windows/desktop/aa367157) MIDL attribute for more information.  
  
 ***custom***  (optional)  
 One or more attributes; this is similar to the [custom](../VS_visualcpp/custom--C---.md) attribute. The first parameter to `custom` is the GUID of the attribute. For example:  
  
```  
[module(custom={guid,1}, custom={guid1,2})]  
```  
  
 **resource_name**  
 The string resource ID of the .rgs file used to register the APP ID of the DLL, executable, or service. When the module is of type service, this argument is also used to obtain the ID of the string containing the service name.  
  
> [!NOTE]
>  Both the .rgs file and the string containing the service name should contain the same numerical value.  
  
## Remarks  
 Unless you specify the **restricted** parameter to [emitidl](../VS_visualcpp/emitidl.md), **module** is required in any program that uses C++ attributes.  
  
 A library block will be created if, in addition to the **module** attribute, source code also uses [dispinterface](../VS_visualcpp/dispinterface.md), [dual](../VS_visualcpp/dual.md), [object](../VS_visualcpp/object--C---.md), or an attribute that implies [coclass](../VS_visualcpp/coclass.md).  
  
 One library block is allowed in an .idl file. Multiple module entries in source code will be merged, with the most recent parameter values being implemented.  
  
 If this attribute is used within a project that uses ATL, the behavior of the attribute changes. In addition to the above behavior, the attribute also inserts a global object (called **_AtlModule**) of the correct type and additional support code. If the attribute is standalone, it inserts a class derived from the correct module type. If the attribute is applied to a class, it adds a base class of the correct module type. The correct type is determined by the value of the `type` parameter:  
  
-   `type` = **dll**  
  
     [CAtlDllModuleT](../VS_visualcpp/CAtlDllModuleT-Class.md) is used as the base class and the standard DLL entry points required for a COM server. These entry points are [DllMain](http://msdn.microsoft.com/library/windows/desktop/ms682583), [DllRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms682162), [DllUnRegisterServer](http://msdn.microsoft.com/library/windows/desktop/ms691457), [DllCanUnloadNow](http://msdn.microsoft.com/library/windows/desktop/ms690368), and [DllGetClassObject](http://msdn.microsoft.com/library/windows/desktop/dd797891).  
  
-   `type` = **exe**  
  
     [CAtlExeModuleT](../VS_visualcpp/CAtlExeModuleT-Class.md) is used as the base class and the standard executable entry point [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **service**  
  
     [CAtlServiceModuleT](../VS_visualcpp/CAtlServiceModuleT-Class.md) is used as the base class and the standard executable entry point [WinMain](http://msdn.microsoft.com/library/windows/desktop/ms633559).  
  
-   `type` = **unspecified**  
  
     Disables injection of ATL code related to the module attribute.  
  
## Example  
 The following code shows how to create a library block in the generated .idl file.  
  
```  
// cpp_attr_ref_module1.cpp  
// compile with: /LD  
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];  
```  
  
 The following code shows that you can provide your own implementation of a function that would appear in the code that was injected as a result of using **module**. See [/Fx](../VS_visualcpp/-Fx--Merge-Injected-Code-.md) for more information on viewing injected code. In order to override one of the functions inserted by the **module** attribute, make a class that will contain your implementation of the function and make the **module** attribute apply to that class.  
  
```  
// cpp_attr_ref_module2.cpp  
// compile with: /LD /link /OPT:NOREF  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
// no semicolon after attribute block  
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]   
// module attribute now applies to this class  
class CMyClass {  
public:  
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {  
   // add your own code here  
   return __super::DllMain(dwReason, lpReserved);  
   }  
};  
```  
  
## Requirements  
  
### Attribute Context  
  
|||  
|-|-|  
|**Applies to**|Anywhere|  
|**Repeatable**|No|  
|**Required attributes**|None|  
|**Invalid attributes**|None|  
  
 For more information, see [Attribute Contexts](../VS_visualcpp/Attribute-Contexts.md).  
  
## See Also  
 [IDL Attributes](../VS_visualcpp/IDL-Attributes.md)   
 [Class Attributes](../VS_visualcpp/Class-Attributes.md)   
 [Stand-Alone Attributes](../VS_visualcpp/Stand-Alone-Attributes.md)   
 [Typedef, Enum, Union, and Struct Attributes](../VS_visualcpp/Typedef--Enum--Union--and-Struct-Attributes.md)   
 [usesgetlasterror](../VS_visualcpp/usesgetlasterror.md)   
 [library](http://msdn.microsoft.com/library/windows/desktop/aa367069)   
 [helpcontext](../VS_visualcpp/helpcontext.md)   
 [helpstring](../VS_visualcpp/helpstring.md)   
 [helpfile](../VS_visualcpp/helpfile.md)   
 [version](../VS_visualcpp/version--C---.md)   
 [Attributes Samples](assetId:///558ebdb2-082f-44dc-b442-d8d33bf7bdb8)