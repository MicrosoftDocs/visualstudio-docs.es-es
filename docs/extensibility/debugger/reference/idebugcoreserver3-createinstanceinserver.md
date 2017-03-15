---
title: "IDebugCoreServer3::CreateInstanceInServer | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
helpviewer_keywords: 
  - "IDebugCoreServer3::CreateInstanceInServer"
ms.assetid: 76f36bae-f6ab-413c-a8a9-8808bfeba05b
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugCoreServer3::CreateInstanceInServer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea una instancia de un motor de depuración en el servidor.  
  
## Sintaxis  
  
```cpp#  
HRESULT CreateInstanceInServer(  
   LPCWSTR  szDll,  
   WORD     wLangId,  
   REFCLSID clsidObject,  
   REFIID   riid,  
   void**   ppvObject  
);  
```  
  
```c#  
int CreateInstanceInServer(  
   string     szDll,   
   ushort     wLangID,   
   ref Guid   clsidObject,   
   ref Guid   riid,   
   out IntPtr ppvObject  
);  
```  
  
#### Parámetros  
 `szDll`  
 \[in\]  La ruta de acceso al archivo DLL que implementa el CLSID especificado en el parámetro de `clsidObject` .  Si es `NULL`, se llama a la función de `CoCreateInstance` de COM.  
  
 `wLangId`  
 \[in\]  Configuración regional del motor de depuración.  Puede ser 0 si se llama al método de [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md) .  
  
 `clsidObject`  
 \[in\]  El CLSID del motor de depuración a crear.  
  
 `riid`  
 \[in\]  Identificador de la interfaz de la interfaz específica a recuperar del objeto de clase.  
  
 `ppvObject`  
 \[out\]  interfaz de `IUnknown` de objeto con instancias.  Convierta o formulario este objeto a la interfaz deseada.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)   
 [SetLocale](../../../extensibility/debugger/reference/idebugengine2-setlocale.md)