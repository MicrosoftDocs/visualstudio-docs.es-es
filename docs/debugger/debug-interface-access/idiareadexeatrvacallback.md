---
title: "IDiaReadExeAtRVACallback | Microsoft Docs"
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
  - "IDiaReadExeAtRVACallback (interfaz)"
ms.assetid: b2892513-3952-4f99-9b98-60cb9b1fdc91
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaReadExeAtRVACallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Permite a una aplicación cliente para proporcionar bytes de un archivo ejecutable especificados por una dirección relativa virtual.  
  
## Sintaxis  
  
```  
IDiaReadExeAtRVACallback : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaReadExeAtRVACallback`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaReadExeAtRVACallback::ReadExecutableAtRVA](../../debugger/debug-interface-access/idiareadexeatrvacallback-readexecutableatrva.md)|Lee el número de bytes especificado a partir de la dirección virtual relativa especificada \(RVA\) del archivo ejecutable.|  
  
## Comentarios  
 La aplicación cliente implementa esta interfaz para proporcionar los bytes del archivo ejecutable mediante una dirección relativa virtual en el archivo ejecutable.  para utilizar un desplazamiento de archivo absoluto, implemente la interfaz de [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) .  
  
## Notas para los llamadores  
 Este método se implementa mediante la aplicación cliente y se pasa a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) el método como un método alternativo para leer el archivo.  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)