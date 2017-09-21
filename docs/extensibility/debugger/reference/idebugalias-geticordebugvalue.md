---
title: "IDebugAlias::GetICorDebugValue | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugAlias::GetICorDebugValue"
helpviewer_keywords: 
  - "IDebugAlias::GetICorDebugValue (método)"
ms.assetid: b9eb39ee-84af-4ace-9cfe-236b3d48aff5
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugAlias::GetICorDebugValue
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera una interfaz de código administrado que representa el valor asociado a este alias.  
  
## Sintaxis  
  
```cpp  
HRESULT GetICorDebugValue(  
   IUnknown** ppUnk  
);  
```  
  
```c#  
int GetICorDebugValue(  
   out object ppUnk  
);  
```  
  
#### Parámetros  
 `ppUnk`  
 \[out\] `IUnknown` interfaz que representa el valor asociado a este alias. Esta interfaz se puede consultar para el `ICorDebugValue` interfaz.  
  
## Valor devuelto  
 Si se realiza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Este método sólo se aplica a valores administrados \(el `ICorDebugValue` está disponible en una interfaz la [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] y se define en el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK en el archivo cordebug.idl\).  
  
## Vea también  
 [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)