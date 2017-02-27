---
title: "IDiaSymbol::get_lowerBoundId | Microsoft Docs"
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
  - "IDiaSymbol::get_lowerBoundId (método)"
ms.assetid: 12ce98e9-a225-4947-88c9-5fda39dd67e4
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_lowerBoundId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el identificador del límite inferior de una dimensión de la matriz de FORTRAN.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_lowerBoundId (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve el identificador del token que representa el límite inferior de una dimensión de la matriz de FORTRAN.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 el identificador es un valor único creado por el diámetro SDK para marcar todos los símbolos como único.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)