---
title: DiaAddressMapEntry | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- DiaAddressMapEntry enumeration
ms.assetid: 5d0ae226-981d-4541-a801-fc4993fe663b
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0a6d5075917c49be66d030846cdc186b0fa5e50a
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580108"
---
# <a name="diaaddressmapentry"></a>DiaAddressMapEntry
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [DiaAddressMapEntry](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/diaaddressmapentry).  
  
Describe una entrada en un mapa de direcciones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
  
1.  Buscar la asignación de la entrada de `e`, con el mayor `rva` menor o igual a `addrA`.  
  
2.  Establecer `delta = addrA – e.rva`.  
  
3.  Establecer `addrB = e.rvaTo + delta`.  
  
 Una matriz de `DiaAddressMapEntry` estructuras se pasa a la [Set_addressmap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: dia2.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaAddressMap::set_addressMap](../../debugger/debug-interface-access/idiaaddressmap-set-addressmap.md)



