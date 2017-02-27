---
title: "IDiaSymbol::get_farReturn | Microsoft Docs"
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
  - "IDiaSymbol::get_farReturn (método)"
ms.assetid: 141df0e9-f4d9-4330-a043-5d9ea865257f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaSymbol::get_farReturn
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un indicador que especifica si la función contiene un aún return.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_farReturn(  
   BOOL *pFlag  
);  
```  
  
#### Parámetros  
 `pFlag`  
 \[in\]  Devuelve `TRUE` si la función utiliza un fuera de vuelta, de lo contrario, devuelve `FALSE`.  
  
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