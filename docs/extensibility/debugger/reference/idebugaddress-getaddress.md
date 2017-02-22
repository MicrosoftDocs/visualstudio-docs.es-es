---
title: "IDebugAddress::GetAddress | Microsoft Docs"
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
  - "IDebugAddress::GetAddress"
helpviewer_keywords: 
  - "IDebugAddress:GetAddress (método)"
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

devuelve una estructura que describe un objeto y su ubicación dentro de su ámbito o contenedor.  
  
## Sintaxis  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```c#  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### Parámetros  
 `pAddress`  
 \[in, out\]  Una estructura de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) se ha finalizado con este método.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 La estructura de [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) se pasa a este método, que a continuación la completa con la información adecuada.  Cómo se interpreta esta información depende del tipo de información devuelto y el propio controlador de símbolos.  Vea [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) para obtener más información.  
  
## Vea también  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)