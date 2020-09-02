---
title: METADATA_ADDRESS_LOCAL | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_ADDRESS_LOCAL
helpviewer_keywords:
- METADATA_ADDRESS_LOCAL structure
ms.assetid: 635f6bc5-c486-4e0e-83db-36f15e543843
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 5928f6092adc62dc8f0eb075f20367c056fc50c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62547174"
---
# <a name="metadata_address_local"></a>METADATA_ADDRESS_LOCAL
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta estructura representa la dirección de una variable local dentro de un ámbito (normalmente una función o un método).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_LOCAL {  
   _mdToken  tokMethod;  
   IUnknown* pLocal;  
   DWORD     dwIndex;  
} METADATA_ADDRESS_LOCAL;  
```  
  
```csharp  
public struct METADATA_ADDRESS_LOCAL {  
   public int    tokMethod;  
   public object pLocal;  
   public uint   dwIndex;  
}  
```  
  
## <a name="terms"></a>Términos  
 tokMethod  
 IDENTIFICADOR del método o función del que forma parte la variable local.  
  
 [C++] `_mdToken` es un `typedef` para un 32 bits `int` .  
  
 pLocal  
 Token cuya dirección representa esta estructura.  
  
 dwIndex  
 Puede ser el índice de esta variable local en el método o la función, o algún otro valor (específico del idioma).  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura forma parte de la Unión de la estructura [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) cuando el `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura se establece en `ADDRESS_KIND_LOCAL` (un valor de la enumeración [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) ).  
  
 `Warning:` [Solo C++]  Si `pLocal` no es null, debe llamar a `Release` en el puntero de token ( `addr` es un campo de la estructura [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) ):  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
