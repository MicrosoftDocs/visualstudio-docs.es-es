---
title: "IDiaSourceFile::get_checksumType | Microsoft Docs"
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
  - "IDiaSourceFile::get_checksumType (método)"
ms.assetid: 4c363e61-a6a9-409a-9cc0-d06eb2bee645
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSourceFile::get_checksumType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera el tipo de la suma de comprobación.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_checksumType (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve el tipo de la suma de comprobación.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 el tipo de la suma de comprobación es un valor que se puede asignar a un algoritmo de suma de comprobación.  Por ejemplo, el formato de archivo PDB standard normalmente puede tener uno de los siguientes valores:  
  
|Tipo de suma de comprobación|etiqueta de CryptoAPI|Descripción|  
|----------------------------------|---------------------------|-----------------|  
|0|\<none\>|Ningún presente de suma de comprobación.|  
|1|`CALG_MD5`|suma de comprobación generada con el algoritmo hash MD5.|  
|2|`CALG_SHA1`|suma de comprobación generada con el algoritmo de hash SHA1.|  
  
 Las etiquetas de `CryptoAPI` son de enumeración de `ALG_ID` .  Para obtener más información sobre algoritmos hash, vea la sección de `CryptoAPI` de Microsoft [!INCLUDE[winsdkshort](../../debugger/debug-interface-access/includes/winsdkshort_md.md)].  
  
 Para obtener los bytes reales de suma de comprobación para el archivo de código fuente, llame al método de [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md) .  
  
## Vea también  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSourceFile::get\_checksum](../../debugger/debug-interface-access/idiasourcefile-get-checksum.md)