---
title: "IDiaReadExeAtRVACallback::ReadExecutableAtRVA | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaReadExeAtRVACallback::ReadExecutableAtRVA (método)"
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Lee el número de bytes especificado a partir de la dirección virtual relativa especificada \(RVA\) del archivo ejecutable.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parámetros  
 `relativeVirtualAddress`  
 \[in\]  El RVA en el archivo ejecutable a iniciar lectura.  
  
 `cbData`  
 \[in\]  Número de bytes que se va a leer.  
  
 `pcbData`  
 \[out\]  Devuelve el número de bytes leídos.  
  
 `data[]`  
 \[in, out\]  Una matriz que se completa con los bytes leídos del archivo.  
  
## Comentarios  
 Este método llama el código de soporte de diámetro para cargar bytes de datos de una aplicación ejecutable mediante una dirección relativa virtual.  Se llama a este método en compatible del método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## Vea también  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)