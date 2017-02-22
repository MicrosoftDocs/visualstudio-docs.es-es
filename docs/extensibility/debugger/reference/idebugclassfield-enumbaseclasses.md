---
title: "IDebugClassField::EnumBaseClasses | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField::EnumBaseClasses"
helpviewer_keywords: 
  - "IDebugClassField::EnumBaseClasses (método)"
ms.assetid: 78749674-ef75-46d3-a1f4-ff33afd90e32
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::EnumBaseClasses
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumerador para las clases base de esta clase.  
  
## Sintaxis  
  
```cpp#  
HRESULT EnumBaseClasses(   
   IEnumDebugFields** ppEnum  
);  
```  
  
```c#  
int EnumBaseClasses(  
   out IEnumDebugFields ppEnum  
);  
```  
  
#### Parámetros  
 `ppEnum`  
 \[out\]  devuelve un objeto de [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) que representa la lista de clases base.  Devuelve un valor NULL si no hay clases base.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK, devuelve S\_SH\_NO\_BASE\_CLASSES si no hay clases base \(y el parámetro de `ppEnum` se establece en un valor nulo\); de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Las clases base del objeto de enumerador se especifican en orden de la clase base más inmediata \(o la derivada\) a la clase base más remota.  Por ejemplo, dadas las clases de C\+\+:  
  
```  
class Root { }  
class Level1 : Root { }  
class Level2 : Level1 { }  
class MyClass : Level2 { }  
```  
  
 La enumeración devolverá las clases base en el orden `Level2`, `Level1`, `Root`.  
  
## Vea también  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)