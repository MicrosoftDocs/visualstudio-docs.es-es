---
title: METADATA_ADDRESS_FIELD | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- METADATA_ADDRESS_FIELD
helpviewer_keywords:
- METADATA_ADDRESS_FIELD structure
ms.assetid: 15ab45fe-6b3b-4e09-880b-31b34f523607
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a7d3a85126d58839da2bd04de32ea4d9dd09c405
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/26/2019
ms.locfileid: "55070895"
---
# <a name="metadataaddressfield"></a>METADATA_ADDRESS_FIELD
Esta estructura representa la dirección de un campo de una clase o estructura.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_FIELD {  
   _mdToken tokField;  
} METADATA_ADDRESS_FIELD  
```  
  
```csharp  
public struct METADATA_ADDRESS_FIELD {  
   public int tokField;  
}  
```  
  
## <a name="terms"></a>Términos  
 tokField  
 El identificador del token de campo.  
  
 [C++] `_mdToken` es un `typedef` para 32 bits `int`.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es parte de la unión en el [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura cuando la `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura está establecida en `ADDRESS_KIND_FIELD` (un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)