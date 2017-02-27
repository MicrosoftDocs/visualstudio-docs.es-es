---
title: "IDiaSymbol::get_relativeVirtualAddress | Microsoft Docs"
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
  - "IDiaSymbol::get_relativeVirtualAddress (método)"
ms.assetid: e37219e3-c021-4057-9ec8-4f7cf3c13a15
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDiaSymbol::get_relativeVirtualAddress
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera la dirección virtual relativa \(RVA\) de la ubicación.  Utilice cuando [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md) se establece en `LocIsStatic`.  
  
## Sintaxis  
  
```cpp#  
HRESULT get_relativeVirtualAddress (   
   DWORD* pRetVal  
);  
```  
  
#### Parámetros  
 `pRetVal`  
 \[out\]  Devuelve la dirección virtual relativa de la ubicación.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve `S_FALSE` o un código de error.  
  
> [!NOTE]
>  Un valor devuelto de `S_FALSE` significa que la propiedad no está disponible para el símbolo.  
  
## Ejemplo  
  
```cpp#  
IDiaSymbol* pSymbol;  
DWORD       rva;  
pSymbol->get_relativeVirtualAddress( &rva );  
```  
  
## Vea también  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [LocationType \(Enumeración\)](../../debugger/debug-interface-access/locationtype.md)