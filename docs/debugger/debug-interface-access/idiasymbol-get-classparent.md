---
title: "IDiaSymbol::get_classParent | Microsoft Docs"
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
  - "IDiaSymbol::get_classParent (método)"
ms.assetid: 99db875a-caae-4d60-ae70-64bc8a9f6fba
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IDiaSymbol::get_classParent
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una referencia al elemento primario de la clase de símbolos.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_classParent (   
   IDiaSymbol** pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve un objeto de [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) que representa el elemento primario de la clase de símbolos.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v7.0|  
  
## Comentarios  
 Documentan los tipos de símbolos que pueden ser elementos primarios de la clase en [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md).  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Jerarquía de clases de tipos de símbolos](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)