---
title: "DiaAddressMapEntry | Microsoft Docs"
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
  - "DiaAddressMapEntry (enumeración)"
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

describe una entrada en una configuración de direcciones.  
  
## Sintaxis  
  
```cpp#  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## Elementos \(Elements\)  
 `rva`  
 Una dirección virtual relativa \(RVA\) de la imagen A.  
  
 `rvaTo`  
 Asignan la dirección relativa virtual `rva` en a b de la imagen.  
  
## Comentarios  
 Una configuración de direcciones proporciona una traducción a partir de un diseño de imagen \(a\) a otro \(b\).  Una matriz de estructuras de `DiaAddressMapEntry` ordenadas por `rva` define una configuración de direcciones.  
  
 Para convertir una dirección, `addrA`, de la imagen A una dirección, `addrB`, en b de la imagen, realiza los pasos siguientes:  
  
1.  Busque el mapa para la entrada, `e`, con `rva` más grande menor o igual que `addrA`.  
  
2.  establezca `delta = addrA – e.rva`.  
  
3.  establezca `addrB = e.rvaTo + delta`.  
  
 Una matriz de estructuras de `DiaAddressMapEntry` se pasa al método de [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) .  
  
## Requisitos  
 encabezado: dia2.h  
  
## Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set\_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)