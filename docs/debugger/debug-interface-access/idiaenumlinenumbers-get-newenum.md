---
title: "IDiaEnumLineNumbers::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumLineNumbers::get__NewEnum (método)"
ms.assetid: 8b15f76b-a431-4f60-8bed-3206256b0d10
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaEnumLineNumbers::get__NewEnum
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
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)