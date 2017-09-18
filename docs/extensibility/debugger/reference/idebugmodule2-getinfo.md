---
title: "IDebugModule2::GetInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugModule2::GetInfo"
helpviewer_keywords: 
  - "Método GetInfo"
  - "IDebugModule2::GetInfo (método)"
ms.assetid: de337e66-294f-4ac9-b21e-71fac7418e36
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugModule2::GetInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

obtiene la información sobre este módulo.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetInfo(   
   MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO*       pInfo  
);  
```  
  
```cpp#  
int GetInfo(   
   enum_MODULE_INFO_FIELDS dwFields,  
   MODULE_INFO[]           pInfo  
);  
```  
  
#### Parámetros  
 `dwFields`  
 \[in\]  Una combinación de marcadores de enumeración de [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) que especifican qué campos de `pInfo` se deben completar.  
  
 `pInfo`  
 \[in, out\]  Una estructura de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) se completa con una descripción del módulo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La estructura de [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md) contiene el nombre del módulo que se muestra en la ventana de **Módulos** .  
  
## Vea también  
 [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)