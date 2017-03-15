---
title: "IDebugExpressionEvaluator2::GetService | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugExpressionEvaluator2::GetService"
  - "GetService"
ms.assetid: f8988a9e-9d18-42af-84a7-55f41e9adf63
caps.latest.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 8
---
# IDebugExpressionEvaluator2::GetService
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Recupera un objeto de servicio dado el identificador único.  
  
## Sintaxis  
  
```cpp#  
HRESULT GetService (  
   GUID        uid,  
   IUnknown ** ppService  
);  
```  
  
```c#  
int GetService (  
   Guid       uid,  
   out object ppService  
);  
```  
  
#### Parámetros  
 `uid`  
 \[in\]  Identificador único del servicio a recuperar.  
  
 `ppService`  
 \[out\]  Devuelve un objeto que representa el servicio.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Esto se puede utilizar por un evaluador de terceros de expresiones para obtener servicios de otro evaluador de expresiones.  Por ejemplo, este método se puede utilizar para obtener la interfaz para el servicio del visualizador de evaluador predeterminado de la expresión.  Los evaluadores de terceros de expresiones son poco proclives a necesitar implementar esta interfaz.  
  
## Vea también  
 [IDebugExpressionEvaluator2](../../../extensibility/debugger/reference/idebugexpressionevaluator2.md)