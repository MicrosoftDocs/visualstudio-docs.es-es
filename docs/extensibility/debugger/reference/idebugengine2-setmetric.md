---
title: "IDebugEngine2::SetMetric | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine2:::SetMetric"
helpviewer_keywords: 
  - "IDebugEngine2:::SetMetric"
ms.assetid: dcda4972-c32e-4693-a0e1-25d5c58b9782
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# IDebugEngine2::SetMetric
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Este método establece un valor de Registro conocido como métrica.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetMetric(  
   LPCOLESTR pszMetric,  
   VARIANT   varValue  
);  
```  
  
```c#  
int SetMetric(  
   string pszMetric,  
   object varValue  
);  
```  
  
#### Parámetros  
 `pszMetric`  
 \[in\]  El nombre métrica.  
  
 `varValue`  
 \[in\]  Especifica el valor métrica.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Una medida es un valor de Registro utilizado para cambiar el comportamiento de un motor de depuración o para anunciar de funcionalidad compatible.  Este método puede reenviar la llamada al formulario adecuado de la función de [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) , `SetMetric`.  
  
## Vea también  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Aplicaciones auxiliares SDK para la depuración](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)