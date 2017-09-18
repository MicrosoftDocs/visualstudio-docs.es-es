---
title: "IDebugProgram2::GetDebugProperty | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgram2::GetDebugProperty"
helpviewer_keywords: 
  - "IDebugProgram2::GetDebugProperty"
ms.assetid: d194224e-f0e6-46ab-85d4-9e2639e28946
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgram2::GetDebugProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene las propiedades del programa.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetDebugProperty(   
   IDebugProperty2** ppProperty  
);  
```  
  
```c#  
int GetDebugProperty(   
   out IDebugProperty2 ppProperty  
);  
```  
  
#### Parámetros  
 `ppProperty`  
 \[out\]  Devuelve un objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) que representa las propiedades del programa.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Las propiedades devueltas por este método son específicas del programa.  Si el programa necesita devolver más de una propiedad, el objeto de [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) devuelto por este método es un contenedor de propiedades adicionales y llamando al método de [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md) devuelve una lista de todas las propiedades.  
  
 Un programa puede exponer cualquier número y tipo de propiedades adicionales que se pueden describir mediante la interfaz de `IDebugProperty2` .  El IDE puede mostrar las propiedades adicionales del programa mediante una interfaz de usuario genérica del explorador de propiedades.  
  
## Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [EnumChildren](../../../extensibility/debugger/reference/idebugproperty2-enumchildren.md)