---
title: UdtKind | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- UdtKind enumeration
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9fb22471cea7cd717b8969682a0e1f643f912150
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58998615"
---
# <a name="udtkind"></a>UdtKind
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Describe la variedad de tipo definido por el usuario (UDT).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
