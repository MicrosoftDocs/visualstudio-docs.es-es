---
title: "IEEVisualizerDataProvider::SetObjectForVisualizer | Microsoft Docs"
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
  - "IEEVisualizerDataProvider::SetObjectForVisualizer"
helpviewer_keywords: 
  - "IEEVisualizerDataProvider::SetObjectForVisualizer (método)"
ms.assetid: 40dad2be-57ff-4f74-9d82-c48039c125c4
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IEEVisualizerDataProvider::SetObjectForVisualizer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

este método cambia el objeto que el visualizador representa.  
  
## Sintaxis  
  
```cpp  
HRESULT SetObjectForVisualizer(  
   IDebugObject*  pNewObject,  
   BSTR*          error,  
   IDebugObject** pException  
);  
```  
  
```c#  
int SetObjectForVisualizer(  
   IDebugObject     pNewObject,  
   out string       error,  
   out IDebugObject pException  
);  
```  
  
#### Parámetros  
 `pNewObject`  
 \[in\]  El objeto al conjunto.  
  
 `error`  
 \[out\]  Si se produjo un error que no es el objeto, esta cadena contiene el mensaje de error.  
  
 `pException`  
 \[out\]  Si se produjo un error, este objeto contiene la información de excepción.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Depende del implementador para determinar cómo se devuelve información de error.  Sin embargo, es posible que algunos llamadores puedan examinar sólo para ver si un objeto de excepción se devolvió las había un error, por lo que este método siempre devuelve un objeto de excepción si se produjo un error.  La cadena de error también debe proporcionarse en caso de que el llamador desee hacer uso de ella.  
  
## Vea también  
 [IEEVisualizerDataProvider](../../../extensibility/debugger/reference/ieevisualizerdataprovider.md)   
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)