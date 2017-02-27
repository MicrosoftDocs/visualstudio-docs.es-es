---
title: "IDiaSymbol::get_isHotpatchable | Microsoft Docs"
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
  - "IDiaSymbol::get_isHotpatchable (método)"
ms.assetid: b7b6f490-1cf2-4a68-9237-b152dac84d3c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_isHotpatchable
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera una marca que indica si el módulo fue compilado con el modificador del compilador [\/hotpatch \(Crear una imagen a la que se puede aplicar una revisión reciente\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image) .  
  
## Sintaxis  
  
```cpp#  
HRESULT get_isHotpatchable(  
   BOOL *pFlag  
);  
```  
  
#### Parámetros  
 `pFlag`  
 \[out\]  devuelve `TRUE` si el módulo es caluroso\-patchable; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o código de error.  
  
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