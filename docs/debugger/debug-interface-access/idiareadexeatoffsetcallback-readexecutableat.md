---
title: "IDiaReadExeAtOffsetCallback::ReadExecutableAt | Microsoft Docs"
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
  - "IDiaReadExeAtOffsetCallback::ReadExecutableAt (método)"
ms.assetid: 30b1cef0-b366-4712-8e89-d21f640964f8
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaReadExeAtOffsetCallback::ReadExecutableAt
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

lee el número de bytes especificado que comienzan en el desplazamiento especificado de un archivo ejecutable.  
  
## Sintaxis  
  
```cpp#  
HRESULT ReadExecutableAt (   
   DWORDLONG fileOffset,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### Parámetros  
 fileOffset  
 \[in\]  Desplazamiento en el archivo ejecutable en la lectura de inicio.  
  
 cbData  
 \[in\]  Número de bytes que se va a leer.  
  
 pcbData  
 \[out\]  Devuelve el número de bytes leídos.  
  
 datos \[\]  
 \[in, out\]  Una matriz que se completa con los bytes leídos desde un archivo.  
  
## Comentarios  
 Este método llama el código de soporte de diámetro para cargar bytes de datos de una aplicación ejecutable mediante un desplazamiento de archivo absoluto.  Se llama a este método en compatible del método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
## Vea también  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)