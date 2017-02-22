---
title: "IDebugObject2::GetBackingFieldForProperty | Microsoft Docs"
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
  - "IDebugObject2::GetBackingFieldForProperty"
helpviewer_keywords: 
  - "IDebugObject2::GetBackingFieldForProperty (método)"
ms.assetid: e72c6338-5573-4fad-8075-f3ade3435424
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::GetBackingFieldForProperty
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Obtiene el campo o la variable \(si existe\) que pueden admitir la propiedad representada por este objeto.  
  
## Sintaxis  
  
```cpp  
HRESULT GetBackingFieldForProperty(  
   IDebugObject2** ppObject  
);  
```  
  
```c#  
int GetBackingFieldForProperty(  
   out IDebugObject2 ppObject  
);  
```  
  
#### Parámetros  
 `ppObject`  
 \[out\]  Un objeto de [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) que describe el campo de respaldo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El objeto de [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md) representa una propiedad de clase desde código administrado, es decir, un método con un descriptor de acceso get y set.  Tales propiedades necesarias normalmente una variable contiene el valor manipulan mediante la propiedad.  Esta variable se conoce como el campo de respaldo.  Si no hay ningún campo de respaldo para el objeto, después asegúrese de devolver un valor NULL: algunos llamadores pueden no prestar atención al valor devuelto pero en su lugar tienen para ver si un valor NULL se devuelve en `ppObject`.  
  
## Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)