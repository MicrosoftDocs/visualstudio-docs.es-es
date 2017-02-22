---
title: "IDebugReference2::SetValueAsReference | Microsoft Docs"
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
  - "IDebugReference2::SetValueAsReference"
helpviewer_keywords: 
  - "IDebugReference2::SetValueAsReference"
ms.assetid: 94a545d2-16b9-45e9-b2e7-4e49ff90aad0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugReference2::SetValueAsReference
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

establece el valor de una referencia de otra referencia.  Reservado para un uso futuro.  
  
## Sintaxis  
  
```cpp#  
HRESULT SetValueAsReference (   
   IDebugReference2** rgpArgs,  
   DWORD              dwArgCount,  
   IDebugReference2*  pValue,  
   DWORD              dwTimeout  
);  
```  
  
```cpp#  
int SetValueAsReference (   
   IDebugReference2[] rgpArgs,  
   uint               dwArgCount,  
   IDebugReference2   pValue,  
   uint               dwTimeout  
);  
```  
  
#### Parámetros  
 `rgpArgs`  
 \[in\]  Matriz de los objetos de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) utilizados para determinar cómo establecer el valor de referencia.  
  
 `dwArgCount`  
 \[in\]  El número de referencias de la matriz.  
  
 `pValue`  
 \[in\]  Un objeto de [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md) de que para establecer el valor de propiedad.  
  
 `dwTimeout`  
 \[in\]  hora máxima, en milisegundos, de esperar antes de volver de este método.  uso `INFINITE` de esperar indefinidamente.  
  
## Valor devuelto  
 Siempre devuelve `E_NOTIMPL`.  
  
## Vea también  
 [IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)