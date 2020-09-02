---
title: METADATA_ADDRESS_RETVAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_RETVAL
helpviewer_keywords:
- METADATA_ADDRESS_RETVAL structure
ms.assetid: 5b0ec0fb-84b3-4ce7-8e24-becf3d881d7d
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f685bcfad5cf576215aa50aa26540ba207de2e0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546868"
---
# <a name="metadata_address_retval"></a>METADATA_ADDRESS_RETVAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta estructura representa un valor devuelto de un método o una función.  
  
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
 IDENTIFICADOR del método para el que se devuelve este valor devuelto.  
  
 dwCorType  
 Tipo base del valor devuelto. Este es un valor de la `CorElementType` enumeración definido en el [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] archivo SDK CorHdr. h.  
  
 dwSigSize  
 Tamaño de la firma del valor devuelto (tal y como se almacena en `rgSig` ).  
  
 rgSig  
 Matriz de bytes que forman la firma del valor devuelto.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura forma parte de la Unión de la estructura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura se establece en `ADDRESS_KIND_RETVAL` (un valor de la enumeración [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
