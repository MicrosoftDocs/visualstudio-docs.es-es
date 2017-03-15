---
title: "IDiaEnumSegments::get__NewEnum | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaEnumSegments::get__NewEnum (método)"
ms.assetid: 504505fa-b35c-402f-a440-8972c589cc5b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumSegments::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera la versión de <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de este enumerador.  
  
## Sintaxis  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Parámetros  
 pRetVal  
 \[out\]  devuelve la interfaz de `IUnknown` que representa la versión de <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de este enumerador.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)