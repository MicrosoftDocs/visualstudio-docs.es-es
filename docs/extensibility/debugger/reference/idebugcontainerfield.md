---
title: "IDebugContainerField | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugContainerField"
helpviewer_keywords: 
  - "Interfaz IDebugContainerField"
ms.assetid: a8bbe061-c382-4fe9-a193-3f7d12216041
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# IDebugContainerField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esta interfaz representa un símbolo o un tipo que son un contenedor para otros símbolos o tipos.  
  
## Sintaxis  
  
```  
IDebugContainerField : IDebugField  
```  
  
## Notas para los implementadores  
 Un proveedor de token implementa esta interfaz en el mismo objeto que implementa la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) .  Esta interfaz es también la clase base para todas las interfaces que representan los contenedores.  
  
## Notas para los llamadores  
 Muchos métodos en las interfaces devuelven esta interfaz.  Puesto que es una clase base para todos los contenedores, interfaces especializadas pueden obtenido de esta interfaz mediante [QueryInterface](/visual-cpp/atl/queryinterface).  Estas interfaces incluyen [IDebugArrayField](../../../extensibility/debugger/reference/idebugarrayfield.md), [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), y [IDebugPropertyField](../../../extensibility/debugger/reference/idebugpropertyfield.md).  
  
## métodos en el orden de Vtable  
 Además de los métodos de la interfaz de [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) , esta interfaz implementa el método siguiente:  
  
|Método|Descripción|  
|------------|-----------------|  
|[EnumFields](../../../extensibility/debugger/reference/idebugcontainerfield-enumfields.md)|Crea un enumerador para los campos del contenedor.|  
  
## Comentarios  
 Matrices \(contenedores para las variables\), las clases \(contenedores de los métodos y variables\) y métodos \(contenedores para los parámetros y variables locales\) son todos los ejemplos de contenedores.  
  
## Requisitos  
 encabezado: sh.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Interfaces de proveedor de símbolos](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)