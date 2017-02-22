---
title: "IDiaDataSource::openSession | Microsoft Docs"
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
  - "IDiaDataSource::openSession (método)"
ms.assetid: a3319ed0-3979-483b-9852-c0af96852c48
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource::openSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Abra una sesión para ver símbolos.  
  
## Sintaxis  
  
```cpp#  
HRESULT openSession (   
   IDiaSession** ppSession  
);  
```  
  
#### Parámetros  
 ppSession  
 \[out\]  Devuelve un objeto de [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que representa la sesión abierta.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra los valores devueltos posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E\_UNEXPECTED|El objeto de [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) no se ha inicializado anteriormente con un origen de símbolos.|  
|E\_INVALIDARG|Parámetro no válido de `ppSession` .|  
|E\_OUTOFMEMORY|Memoria insuficiente para abrir la sesión.|  
  
## Comentarios  
 este método abre un objeto de [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para un origen de datos.  
  
 los objetos de`IDiaSession` implementan consultas en el origen de datos.  Una sesión controla un espacio de direcciones para cada conjunto de símbolos de depuración.  Si el archivo .exe o .dll descrito por los símbolos del origen de datos está activo en intervalos con varias direcciones \(por ejemplo, porque varios procesos lo tienen carga\), entonces una sesión para cada intervalo de dirección debe utilizarse.  
  
## Ejemplo  
  
```cpp#  
IDiaSession* pSession;  
HRESULT hr = pSource->openSession( &pSession );  
if (FAILED(hr))  
{  
   // report error  
}  
```  
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)