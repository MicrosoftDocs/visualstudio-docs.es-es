---
title: METADATA_ADDRESS_METHOD | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_METHOD
helpviewer_keywords: METADATA_ADDRESS_METHOD structure
ms.assetid: fc0e5370-1b4f-4867-837f-0d63c4b9dd09
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: d94087b9408afcc82dda8715faa643fa4f348cf0
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="metadataaddressmethod"></a>METADATA_ADDRESS_METHOD
Esta estructura representa la dirección de un método de una clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_METHOD {  
   _mdToken tokMethod;  
   DWORD    dwOffset;  
   DWORD    dwVersion;  
} METADATA_ADDRESS_METHOD;  
```  
  
```csharp  
public struct METADATA_ADDRESS_METHOD {  
   public int  tokMethod;  
   public uint dwOffset;  
   public uint dwVersion;  
}  
```  
  
## <a name="terms"></a>Términos  
 tokMethod  
 El identificador del método.  
  
 [C++] `_mdToken` es un `typedef` de 32 bits `int`.  
  
 dwOffset  
 El desplazamiento desde el principio de la clase a este método (puede representar la posición de desplazamiento en vtable).  
  
 dwVersion  
 La versión del método (este valor es único para el proveedor de símbolos).  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es una parte de la unión en el [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura cuando la `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura está establecida en `ADDRESS_KIND_METHOD` (un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)