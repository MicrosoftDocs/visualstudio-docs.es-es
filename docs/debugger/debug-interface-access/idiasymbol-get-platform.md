---
title: "IDiaSymbol::get_platform | Microsoft Docs"
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
  - "IDiaSymbol::get_platform (método)"
ms.assetid: dff1c1eb-bcb2-4275-bb07-f2fdc076d6fb
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IDiaSymbol::get_platform
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la plataforma escrita para la que el compilando fue compilado.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_platform (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve un valor de enumeración de [CV\_CPU\_TYPE\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-cpu-type-e.md) que especifica la plataforma escrita para la que el compilando fue compilado.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [CV\_CPU\_TYPE\_e \(Enumeración\)](../../debugger/debug-interface-access/cv-cpu-type-e.md)