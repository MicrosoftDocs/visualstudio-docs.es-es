---
title: "IDiaLoadCallback::NotifyDebugDir | Microsoft Docs"
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
  - "IDiaLoadCallback::NotifyDebugDir (método)"
ms.assetid: bd04e2f6-0dbf-4742-a556-96f2cd99aa19
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaLoadCallback::NotifyDebugDir
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Llamado cuando un directorio debug se encontró en el archivo .exe.  
  
## Sintaxis  
  
```cpp#  
HRESULT NotifyDebugDir (   
   BOOL  fExecutable,  
   DWORD cbData,  
   BYTE  data[]  
);  
```  
  
#### Parámetros  
 `fExecutable`  
 \[in\]  `TRUE` si el directorio de depuración se lee de una aplicación ejecutable \(en lugar de un archivo .dbg\).  
  
 `cbData`  
 \[in\]  Recuento de bytes de datos en el directorio de depuración.  
  
 `data[]`  
 \[in\]  Una matriz que se completa con el directorio debug.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  El código devuelto se omite normalmente.  
  
## Comentarios  
 El método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) invoca esta devolución de llamada cuando encuentra un directorio de depuración al procesar el archivo ejecutable.  
  
 Este método quita la necesidad del cliente en ingeniería inversa la aplicación ejecutable o el archivo de depuración para admitir la información de depuración distinto de que encontró en el archivo .pdb.  Con estos datos, el cliente puede reconocer el tipo de información de depuración disponible y si se encuentra en el archivo ejecutable o el archivo .dbg.  
  
 La mayoría de los clientes no necesitarán esta devolución de llamada porque abre el método de `IDiaDataSource::loadDataForExe` transparente .pdb y archivos .dbg cuando sea necesario para atender símbolos.  
  
## Vea también  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)