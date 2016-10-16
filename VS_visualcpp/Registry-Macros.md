---
title: "Registry Macros"
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
ms.topic: reference
ms.assetid: 3ee041da-c63b-42a4-89cf-2a4b2a6f81ae
caps.latest.revision: 11
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
# Registry Macros
These macros define useful type library and registry facilities.  
  
|||  
|-|-|  
|[_ATL_STATIC_REGISTRY](../Topic/_ATL_STATIC_REGISTRY.md)|Indicates that you want the registration code for your object to be in the object to avoid a dependency on ATL.DLL.|  
|[DECLARE_LIBID](../Topic/DECLARE_LIBID.md)|Provides a way for ATL to obtain the                             *libid* of the type library.|  
|[DECLARE_NO_REGISTRY](../Topic/DECLARE_NO_REGISTRY.md)|Avoids default ATL registration.|  
|[DECLARE_REGISTRY](../Topic/DECLARE_REGISTRY.md)|Enters or removes the main object's entry in the system registry.|  
|[DECLARE_REGISTRY_APPID_RESOURCEID](../Topic/DECLARE_REGISTRY_APPID_RESOURCEID.md)|Specifies the information required to automatically register the                             *appid*.|  
|[DECLARE_REGISTRY_RESOURCE](../Topic/DECLARE_REGISTRY_RESOURCE.md)|Finds the named resource and runs the registry script within it.|  
|[DECLARE_REGISTRY_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md)|Finds the resource identified by an ID number and runs the registry script within it.|  
  
##  <a name="_atl_static_registry"></a>  _ATL_STATIC_REGISTRY  
 A symbol that indicates you want the registration code for your object to be in the object to avoid a dependency on ATL.DLL.  
  
```  
  
#define _ATL_STATIC_REGISTRY  
  
```  
  
### Remarks  
 When you define                         **ATL_STATIC_REGISTRY**, you should use the following code:  
  
 [!CODE [NVC_ATL_EventHandlingSample#5](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_EventHandlingSample#5)]  
  
##  <a name="declare_libid"></a>  DECLARE_LIBID  
 Provides a way for ATL to obtain the                 *libid* of the type library.  
  
```  
  
DECLARE_LIBID(Â   
   libid Â   
)  
  
```  
  
### Parameters  
 *libid*  
 The GUID of the type library.  
  
### Remarks  
 Use                         `DECLARE_LIBID` in a                         `CAtlModuleT`-derived class.  
  
### Example  
 Non-attributed wizard-generated ATL projects will have a sample of using this macro.  
  
##  <a name="declare_no_registry"></a>  DECLARE_NO_REGISTRY  
 Use                 `DECLARE_NO_REGISTRY` if you want to avoid any default ATL registration for the class in which this macro appears.  
  
```  
  
DECLARE_NO_REGISTRY( )  
  
```  
  
##  <a name="declare_registry"></a>  DECLARE_REGISTRY  
 Enters the standard class registration into the system registry or removes it from the system registry.  
  
```  
  
DECLARE_REGISTRY(Â   
   class  
,Â   
   pid  
,Â   
   vpid  
,Â   
   nid  
,Â   
   flags Â   
)  
  
```  
  
### Parameters  
 `class`  
 [in] Included for backward compatibility.  
  
 `pid`  
 [in] An                                 `LPCTSTR` that is a version-specific program identifier.  
  
 *vpid*  
 [in] An                                 `LPCTSTR` that is a version-independent program identifier.  
  
 *nid*  
 [in] A                                 **UINT** that is an index of the resource string in the registry to use as the description of the program.  
  
 `flags`  
 [in] A                                 `DWORD` containing the program's threading model in the registry. Must be one of the following values:                                 **THREADFLAGS_APARTMENT**,                                 **THREADFLAGS_BOTH**, or                                 **AUTPRXFLAG**.  
  
### Remarks  
 The standard registration consists of the CLSID, program ID, version-independent program ID, description string, and thread model.  
  
 When you create an object or control using the ATL Add Class Wizard, the wizard automatically implements script-based registry support and adds the                         [DECLARE_REGISTRY_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) macro to your files. If you do not want script-based registry support, you need to replace this macro with                         `DECLARE_REGISTRY`.                         `DECLARE_REGISTRY` only inserts the five basic keys described above into the registry. You must manually write code to insert other keys into the registry.  
  
##  <a name="declare_registry_appid_resourceid"></a>  DECLARE_REGISTRY_APPID_RESOURCEID  
 Specifies the information required to automatically register the                 *appid*.  
  
```  
  
DECLARE_REGISTRY_APPID_RESOURCEID(Â   
   resid  
,Â   
   appid Â   
)  
  
```  
  
### Parameters  
 *resid*  
 The resource id of the .rgs file that contains information about the                                 *appid*.  
  
 *appid*  
 A GUID.  
  
### Remarks  
 Use                         `DECLARE_REGISTRY_APPID_RESOURCEID` in a                         `CAtlModuleT`-derived class.  
  
### Example  
 Classes added to ATL projects with the Add Class code wizard will have a sample of using this macro.  
  
##  <a name="declare_registry_resource"></a>  DECLARE_REGISTRY_RESOURCE  
 Gets the named resource containing the registry file and runs the script to either enter objects into the system registry or remove them from the system registry.  
  
```  
  
DECLARE_REGISTRY_RESOURCE(Â   
   x Â   
)  
  
```  
  
### Parameters  
 *x*  
 [in] String identifier of your resource.  
  
### Remarks  
 When you create an object or control using the ATL Project Wizard, the wizard will automatically implement script-based registry support and add the                         [DECLARE_REGISTRY_RESOURCEID](../Topic/DECLARE_REGISTRY_RESOURCEID.md) macro, which is similar to                         `DECLARE_REGISTRY_RESOURCE`, to your files.  
  
 You can statically link with the ATL Registry Component (Registrar) for optimized registry access. To statically link to the Registrar code, add the following line to your stdafx.h file:  
  
 [!CODE [NVC_ATL_COM#56](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#56)]  
  
 If you want ATL to substitute replacement values at run time, do not specify the                         `DECLARE_REGISTRY_RESOURCE` or                         `DECLARE_REGISTRY_RESOURCEID` macro. Instead, create an array of                         **_ATL_REGMAP_ENTRIES** structures, where each entry contains a variable placeholder paired with a value to replace the placeholder at run time. Then call                         [CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md) or                         [CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md), passing the array. This adds all of the replacement values in the                         **_ATL_REGMAP_ENTRIES** structures to the Registrar's replacement map.  
  
 For more information about replaceable parameters and scripting, see the article                         [The ATL Registry Component (Registrar)](../VS_visualcpp/ATL-Registry-Component--Registrar-.md).  
  
##  <a name="declare_registry_resourceid"></a>  DECLARE_REGISTRY_RESOURCEID  
 Same as                 [DECLARE_REGISTRY_RESOURCE](../Topic/DECLARE_REGISTRY_RESOURCE.md) except that it uses a wizard-generated                 **UINT** to identify the resource, rather than a string name.  
  
```  
  
DECLARE_REGISTRY_RESOURCEID(Â   
   x Â   
)  
  
```  
  
### Parameters  
 *x*  
 [in] Wizard-generated identifier of your resource.  
  
### Remarks  
 When you create an object or control using the ATL Project Wizard, the wizard will automatically implement script-based registry support and add the                         `DECLARE_REGISTRY_RESOURCEID` macro to your files.  
  
 You can statically link with the ATL Registry Component (Registrar) for optimized registry access. To statically link to the Registrar code, add the following line to your stdafx.h file:  
  
 [!CODE [NVC_ATL_COM#56](../CodeSnippet/VS_Snippets_Cpp/NVC_ATL_COM#56)]  
  
 If you want ATL to substitute replacement values at run time, do not specify the                         `DECLARE_REGISTRY_RESOURCE` or                         `DECLARE_REGISTRY_RESOURCEID` macro. Instead, create an array of                         **_ATL_REGMAP_ENTRIES** structures, where each entry contains a variable placeholder paired with a value to replace the placeholder at run time. Then call                         [CAtlModule::UpdateRegistryFromResourceD](../Topic/CAtlModule::UpdateRegistryFromResourceD.md) or                         [CAtlModule::UpdateRegistryFromResourceS](../Topic/CAtlModule::UpdateRegistryFromResourceS.md), passing the array. This adds all of the replacement values in the                         **_ATL_REGMAP_ENTRIES** structures to the Registrar's replacement map.  
  
 For more information about replaceable parameters and scripting, see the article                         [The ATL Registry Component (Registrar)](../VS_visualcpp/ATL-Registry-Component--Registrar-.md).  
  
## See Also  
 [Macros](../VS_visualcpp/ATL-Macros.md)