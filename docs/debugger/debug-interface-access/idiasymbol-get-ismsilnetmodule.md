---
title: "IDiaSymbol::get_isMSILNetmodule | Microsoft Docs"
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
  - "IDiaSymbol::get_isMSILNetmodule (método)"
ms.assetid: 593827f3-8437-4a12-ada4-ff715ec95fb2
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# IDiaSymbol::get_isMSILNetmodule
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una marca que indica si el módulo es En.  netmodule \(un módulo de Lenguaje intermedio de Microsoft \(MSIL\) que solo contiene metadatos ni símbolos nativos\).  
  
## Sintaxis  
  
```cpp#  
HRESULT get_isMSILNetmodule(  
   BOOL *pFlag  
);  
```  
  
#### Parámetros  
 `pFlag`  
 \[out\]  devuelve `TRUE` si el módulo es MSIL; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 Esta propiedad está disponible en el tipo de token de `SymTagCompilandDetails` \(vea [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)\).  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v8.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CompilandDetails](../../debugger/debug-interface-access/compilanddetails.md)