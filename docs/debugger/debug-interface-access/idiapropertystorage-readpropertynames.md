---
title: "IDiaPropertyStorage::ReadPropertyNames | Microsoft Docs"
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
  - "IDiaPropertyStorage::ReadPropertyNames"
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera que se corresponden con los nombres de cadena para los identificadores especificados de la propiedad.  
  
## Sintaxis  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### Parámetros  
 `cpropid`  
 \[in\]  número de id. de la propiedad en `rgpropid`.  
  
 `rgpropid`  
 \[in\]  Matriz de los id. de la propiedad para que obtienen los nombres \(`PROPID` se define en WTypes.h como `ULONG`\).  
  
 `rglpwstrName`  
 \[in, out\]  Matriz de los nombres de propiedad para los identificadores. especificados de la propiedad.  La matriz se debe reservar para contener el número solicitado de nombres y debe poder contener por lo menos las cadenas de `cpropid``BSTR` .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; si no devuelve un código de error.  
  
## Comentarios  
 Los nombres de propiedad devueltos deben ser liberados \(llamando a la función de `SysFreeString` \) cuando ya no se necesiten.  
  
## Vea también  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)