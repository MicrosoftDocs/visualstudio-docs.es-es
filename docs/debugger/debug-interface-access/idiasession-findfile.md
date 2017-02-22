---
title: "IDiaSession::findFile | Microsoft Docs"
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
  - "IDiaSession::findFile (método)"
ms.assetid: a215dc21-b316-40d7-9923-55bfa014976b
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findFile
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Archivos de código fuente de recupera por el compilando y nombre.  
  
## Sintaxis  
  
```cpp#  
HRESULT findFile (   
   IDiaSymbol*           pCompiland,  
   LPCOLESTR             name,  
   DWORD                 option,  
   IDiaEnumSourceFiles** ppResult  
);  
```  
  
#### Parámetros  
 `pCompiland`  
 \[in\] objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el compilando que se utilizará como contexto para la búsqueda.  Establezca este parámetro en `NULL` para buscar archivos de código fuente en todos los elementos.  
  
 `name`  
 \[in\] especifica el nombre del archivo de código fuente que se va a recuperar.  Establezca este parámetro en `NULL` para que todos los archivos de código fuente se recuperen.  
  
 `option`  
 \[in\] especifica las opciones de comparación aplicado para llamar a buscar.  Los valores de enumeración de [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md) sólo se pueden utilizar o en combinación.  
  
 `ppResult`  
 \[out\] devuelve un objeto de [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md) que contiene una lista de los archivos de código fuente recuperados.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  
  
## Ejemplo  
  
```cpp#  
IDiaEnumSourceFiles* pEnum;  
pSession->findFile( NULL, L"sourcefile.cpp", nsFNameExt, &pEnum );  
```  
  
## Vea también  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [NameSearchOptions \(Enumeración\)](../../debugger/debug-interface-access/namesearchoptions.md)