---
title: "IDiaSymbol::get_registerId | Microsoft Docs"
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
  - "IDiaSymbol::get_registerId (método)"
ms.assetid: f881e793-eb9e-48dc-a847-dd61d77174fc
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_registerId
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera el designador de registro de la ubicación en [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md) se establece en `LocIsEnregistered`.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_registerId (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  devuelve el designador de registro de la ubicación.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Comentarios  
 Si el símbolo está en relación con un registro, es decir, si [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md) de símbolos se establece en `LocIsRegRel`, utilice el método de `get_registerId` seguido por una llamada al método de [IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md) para obtener el desplazamiento de registro donde se encuentra el símbolo.  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md)