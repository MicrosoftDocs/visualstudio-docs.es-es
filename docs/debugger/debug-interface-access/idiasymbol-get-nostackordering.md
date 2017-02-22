---
title: "IDiaSymbol::get_noStackOrdering | Microsoft Docs"
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
  - "IDiaSymbol::get_noStackOrdering (método)"
ms.assetid: a1753917-705b-4165-9880-d05e91e6dcb4
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_noStackOrdering
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta función recupera una marca que indica si el ningún orden de pila puede realizarse como parte de comprobar de búfer de la pila \(opción del compilador[\/GS \(Comprobación de seguridad del búfer\)](/visual-cpp/build/reference/gs-buffer-security-check) \).  
  
## Sintaxis  
  
```cpp#  
HRESULT get_noStackOrdering(  
   BOOL *pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve `TRUE` si el ningún orden de pila puede realizarse como parte de comprobar de búfer de la pila; de lo contrario, devuelve `FALSE`.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Requisitos  
  
|Requisito|Descripción|  
|---------------|-----------------|  
|encabezado:|dia2.h|  
|versión:|diámetro SDK v8.0|  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [\/GS \(Comprobación de seguridad del búfer\)](/visual-cpp/build/reference/gs-buffer-security-check)