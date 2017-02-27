---
title: "IDiaSymbol::get_container | Microsoft Docs"
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
  - "IDiaSymbol::get_container (método)"
ms.assetid: 24e832eb-80b3-484c-a41b-11477ec9de99
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_container
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta función recupera un puntero a un símbolo que representa el elemento primario del contenedor de este símbolo.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_container(  
   IDiaSymbol **pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve un puntero a `IDiaSymbol` que contiene información sobre el contenedor de este símbolo.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve S\_OK; si no, devuelve S\_FALSE o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de S\_FALSE significa que la propiedad no está disponible para el símbolo.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v8.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)