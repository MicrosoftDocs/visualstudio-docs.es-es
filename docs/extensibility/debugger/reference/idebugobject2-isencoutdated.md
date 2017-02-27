---
title: "IDebugObject2::IsEncOutdated | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugObject2::IsEncOutdated"
helpviewer_keywords: 
  - "IDebugObject2::IsEncOutdated (método)"
ms.assetid: d3a8c02d-895b-478c-9957-d663130f308e
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugObject2::IsEncOutdated
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método determina si el estado de editar y continuar de este objeto o contenedor primario es obsoleta.  Un evaluador de expresiones personalizado no implementa este método y no siempre devuelve `E_NOTIMPL`.  
  
## Sintaxis  
  
```cpp  
HRESULT IsEncOutdated(  
   BOOL* pfEncOutdated  
);  
```  
  
```c#  
int IsEncOutdated(  
   out int pfEncOutdated  
);  
```  
  
#### Parámetros  
 `pfEncOutdated`  
 \[out\]  Cero \(`TRUE`\) si el estado de editar y continuar no está actualizada, cero \(`FALSE`\) si no es.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
> [!NOTE]
>  Un evaluador de expresiones personalizado siempre debe devolver `E_NOTIMPL`.  
  
## Vea también  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)