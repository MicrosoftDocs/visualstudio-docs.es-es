---
title: "IDiaEnumSourceFiles::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumSourceFiles::get__NewEnum (método)"
ms.assetid: 8405966c-64b4-4743-9a83-0e27ca2047c7
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumSourceFiles::get__NewEnum
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
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)