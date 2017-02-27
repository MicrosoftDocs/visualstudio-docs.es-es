---
title: "IDiaEnumTables::get__NewEnum | Microsoft Docs"
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
  - "IDiaEnumTables::get__NewEnum (método)"
ms.assetid: 7b1159c7-a5f0-4baa-861a-dc11437d8b93
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaEnumTables::get__NewEnum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera la versión de <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de este enumerador.  
  
## Sintaxis  
  
```cpp#  
HRESULT get__NewEnum (   
   IUnknown** pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve la interfaz de `IUnknown` que representa la versión de <xref:System.Runtime.InteropServices.ComTypes.IEnumVARIANT> de este enumerador.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Vea también  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)