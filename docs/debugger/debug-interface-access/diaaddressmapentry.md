---
title: DiaAddressMapEntry | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 501defcd2274ab32624a97b9a1463e8f4a515c1e
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49819061"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
Describe una entrada en un mapa de direcciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
struct DiaAddressMapEntry {   
   DWORD rva,  
   DWORD rvaTo  
};  
```  
  
## <a name="elements"></a>Elementos  
 `rva`  
 Una dirección virtual relativa (RVA) en la imagen A.  
  
 `rvaTo`  
 La dirección virtual relativa `rva` está asignado a en imagen B.  
  
## <a name="remarks"></a>Comentarios  
 Un mapa de direcciones proporciona una traducción del diseño de una imagen (A) a otro (B). Una matriz de `DiaAddressMapEntry` estructuras ordenadas por `rva` define un mapa de direcciones.  
  
 Para convertir una dirección, `addrA`, en la imagen A una dirección, `addrB`, en la imagen de B, realice los pasos siguientes:  
  
1. Buscar la asignación de la entrada de `e`, con el mayor `rva` menor o igual a `addrA`.  
  
2. Establecer `delta = addrA - e.rva`.  
  
3. Establecer `addrB = e.rvaTo + delta`.  
  
   Una matriz de `DiaAddressMapEntry` estructuras se pasa a la [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dia2.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)