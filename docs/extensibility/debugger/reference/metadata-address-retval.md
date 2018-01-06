---
title: METADATA_ADDRESS_RETVAL | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: METADATA_ADDRESS_RETVAL
helpviewer_keywords: METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 4de62d86bcb8453c4bdd01fc697390d1c55d9dd5
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="metadataaddressretval"></a>METADATA_ADDRESS_RETVAL
Esta estructura representa un valor devuelto de un método o función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_RETVAL {  
   _mdToken tokMethod;  
   DWORD    dwCorType;  
   DWORD    dwSigSize;  
   BYTE     rgSig[10];  
} METADATA_ADDRESS_RETVAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_RETVAL {  
   public int    tokMethod;  
   public uint   dwCorType;  
   public uint   dwSigSize;  
   public byte[] rgSig;  
}  
```  
  
## <a name="terms"></a>Términos  
 tokMethod  
 El identificador del método que este valor devuelto es para.  
  
 dwCorType  
 El tipo base del valor devuelto. Se trata de un valor de la `CorElementType` enumeración definida en el [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] archivo corhdr.h del SDK.  
  
 dwSigSize  
 El tamaño de la firma del valor devuelto (tal como se almacena en `rgSig`).  
  
 rgSig  
 Una matriz de bytes que forman la firma del valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es una parte de la unión en el [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura cuando la `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura está establecida en `ADDRESS_KIND_RETVAL` (un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)