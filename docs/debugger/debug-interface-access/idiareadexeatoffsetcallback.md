---
title: "IDiaReadExeAtOffsetCallback | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback (interfaz)"
ms.assetid: 3c961641-3ce3-4bc3-bd6e-a802fa3bec49
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaReadExeAtOffsetCallback
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Permite a una aplicación cliente para proporcionar bytes de un archivo ejecutable según lo especificado por la posición del archivo.  
  
## Sintaxis  
  
```  
IDiaReadExeAtOffsetCallback : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaReadExeAtOffsetCallback`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaReadExeAtOffsetCallback::ReadExecutableAt](../../debugger/debug-interface-access/idiareadexeatoffsetcallback-readexecutableat.md)|lee el número de bytes especificado que comienzan en el desplazamiento especificado de un archivo ejecutable.|  
  
## Comentarios  
 La aplicación cliente implementa esta interfaz para proporcionar los bytes del archivo ejecutable mediante una diferencia absoluta en el archivo ejecutable.  Para utilizar una dirección relativa virtual, implemente la interfaz de [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .  
  
## Notas para los llamadores  
 Este método se implementa mediante la aplicación cliente y se pasa a [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) el método como un método alternativo para leer el archivo.  
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)