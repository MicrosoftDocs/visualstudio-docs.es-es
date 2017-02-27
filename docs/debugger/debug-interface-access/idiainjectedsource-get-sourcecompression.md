---
title: "IDiaInjectedSource::get_sourceCompression | Microsoft Docs"
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
  - "IDiaInjectedSource::get_sourceCompression (método)"
ms.assetid: 854b142f-23a9-466c-bf7f-98e581d5abcd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaInjectedSource::get_sourceCompression
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el mensaje de compresión de origen usada.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_sourceCompression (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve el mensaje de compresión de origen usada.  El valor cero indica que no se utiliza ninguna compresión de origen.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`.  devuelve `S_FALSE` si esta propiedad no se admite.  De lo contrario, devuelve un código de error.  
  
## Comentarios  
 El valor devuelto por este método es específico del compilador usado.  Por ejemplo, un compilador podría utilizar codificación o la compresión Ejecutada\-Length de Huffman\-estilo.  
  
## Vea también  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)