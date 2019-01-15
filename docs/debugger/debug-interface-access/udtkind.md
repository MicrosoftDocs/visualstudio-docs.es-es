---
title: UdtKind | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 35631a3913f067e6520da630cd49969d8a2b40f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53924233"
---
# <a name="udtkind"></a>UdtKind
Describe la variedad de tipo definido por el usuario (UDT).  
  
## <a name="syntax"></a>Sintaxis  
  
```C++  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## <a name="elements"></a>Elementos  
 UdtStruct  
 UDT es una estructura.  
  
 UdtClass  
 UDT es una clase.  
  
 UdtUnion  
 UDT es una unión.  
  
 UdtInterface  
 UDT es una interfaz.  
  
## <a name="remarks"></a>Comentarios  
 Devuelven los valores de esta enumeración la [Get_udtkind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: cvconst.h  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)