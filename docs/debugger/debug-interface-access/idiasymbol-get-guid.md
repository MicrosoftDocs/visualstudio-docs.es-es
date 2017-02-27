---
title: "IDiaSymbol::get_guid | Microsoft Docs"
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
  - "IDiaSymbol::get_guid (método)"
ms.assetid: c02a6c92-f406-4646-82e7-3cd005af900e
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_guid
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el identificador único global de símbolos \(GUID\).  
  
## Sintaxis  
  
```cpp#  
HRESULT get_guid (   
   GUID* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve el GUID del símbolo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v7.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)