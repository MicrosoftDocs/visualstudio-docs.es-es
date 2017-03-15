---
title: "IDiaSourceFile::get_checksum | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksum (método)"
ms.assetid: aad63a7e-4e22-44e4-8a5b-81b5174ced1e
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera los bytes de la suma de comprobación.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_checksum (   
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### Parámetros  
 `cbData`  
 \[in\]  Tamaño del búfer de datos, en bytes.  
  
 `pcbData`  
 \[out\]  Devuelve el número de bytes de suma de comprobación.  Este parámetro no puede ser `NULL`.  
  
 `data`  
 \[in, out\]  un búfer que se rellena con los bytes de la suma de comprobación.  Si este parámetro es `NULL`, después `pcbData` devuelve el número de bytes necesarios.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 Para determinar el tipo de algoritmo de suma de comprobación utilizado para generar los bytes de la suma de comprobación, llame al método de [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md) .  
  
 La suma de comprobación se genera normalmente del archivo de código fuente para que los cambios en el archivo de código fuente se reflejan los cambios en los bytes de la suma de comprobación.  Si no coinciden los bytes de la suma de comprobación una suma de comprobación representado de la imagen carga de archivo, el archivo se debe considerar dañado o manipular.  
  
 Las sumas de comprobación típicas nunca son más de 32 bytes de tamaño pero no se supone que el tamaño máximo de una suma de comprobación.  Establezca el parámetro de `data` a `NULL` para obtener el número de bytes necesarios para recuperar la suma de comprobación.  Después asigna un búfer de tamaño adecuado y llame a este método una vez más con el nuevo búfer.  
  
## Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksumType](../../debugger/debug-interface-access/idiasourcefile-get-checksumtype.md)