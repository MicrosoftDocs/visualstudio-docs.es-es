---
title: "IDiaSession::findFileById | Microsoft Docs"
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
  - "IDiaSession::findFileById (método)"
ms.assetid: 710efe04-78b5-4f3e-a1d8-f9b069063503
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSession::findFileById
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

recupera un archivo de código fuente por el identificador de archivo de código fuente.  
  
## Sintaxis  
  
```cpp#  
HRESULT findFileById (   
   DWORD            uniqueId,  
   IDiaSourceFile** ppResult  
);  
```  
  
#### Parámetros  
 `uniqueId`  
 \[in\]  especifica el identificador de archivo de código fuente.  
  
 `ppResult`  
 \[out\]  Devuelve un objeto de [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) que representa el archivo de código fuente recuperado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Comentarios  
 El identificador de archivo de código fuente es un valor único utilizado internamente el diámetro SDK para que todos los archivos de código fuente únicos.  Este método se utiliza normalmente internamente el diámetro SDK.  
  
## Vea también  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)