---
title: "IDiaSymbol::get_isAggregated | Microsoft Docs"
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
  - "IDiaSymbol::get_isAggregated (método)"
ms.assetid: 24d280ef-6ea3-4958-9418-4ad3ca7c67c1
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_isAggregated
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un indicador que especifica si el símbolo de datos forma parte de un agregado o una colección de símbolos; el compilador tratará símbolos agregados como entidades independientes, pero en realidad son parte de un único símbolo mayor.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_isAggregated(  
   BOOL *pFlag  
);  
```  
  
#### Parámetros  
 `pFlag`  
 \[out\]  Devuelve `TRUE` si los datos son parte de una agregación de la división de los símbolos de un símbolo primario; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 el método de [IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md) es `TRUE` para el símbolo que es el elemento primario de los símbolos agregados.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v8.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)