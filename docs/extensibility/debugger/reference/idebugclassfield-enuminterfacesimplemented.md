---
title: "IDebugClassField::EnumInterfacesImplemented | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumInterfacesImplemented"
helpviewer_keywords: 
  - "IDebugClassField::EnumInterfacesImplemented (método)"
ms.assetid: e5523e45-d350-491e-a92c-fe0ca97d2052
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumInterfacesImplemented
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para las interfaces implementadas por esta clase.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumInterfacesImplemented(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumInterfacesImplemented(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de interfaces implementadas.  Devuelve un valor NULL si no hay interfaces.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK o devuelve S\_FALSE si no hay interfaces implementadas en esta clase.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 cada elemento de la enumeración es un objeto de [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) que describe una interfaz.  Observe que el código no administrado de [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] no utiliza interfaces como una entidad única de modo que este método siempre devuelve un valor NULL para el código no administrado de [!INCLUDE[vcprvc](../../../code-quality/includes/vcprvc_md.md)] .  
  
## Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)