---
title: METADATA_ADDRESS_ARRAYELEM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- METADATA_ADDRESS_ARRAYELEM
helpviewer_keywords:
- METADATA_ADDRESS_ARRAYELEM structure
ms.assetid: 24321be5-7c17-4038-82a1-c20a2b68ff3c
caps.latest.revision: 6
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: df941d56a1b9baf8ffa15b022e0b9577da143fc8
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="metadataaddressarrayelem"></a>METADATA_ADDRESS_ARRAYELEM
Esta estructura representa un elemento de matriz dentro de una matriz.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagMETADATA_ADDRESS_ARRAYELEM {  
   _mdToken tokMethod;  
   DWORD    dwIndex;  
} METADATA_ADDRESS_ARRAYELEM;  
```  
  
```csharp  
public struct METADATA_ADDRESS_ARRAYELEM {  
   public int  tokMethod;  
   public uint dwIndex;  
}  
```  
  
## <a name="terms"></a>Términos  
 tokMethod  
 El identificador de la matriz de este elemento es una parte de.  
  
 [C++] `_mdToken` es un `typedef` de 32 bits `int`.  
  
 dwIndex  
 El índice de este elemento de la matriz.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es una parte de la unión en el [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) estructura cuando la `dwKind` campo de la `DEBUG_ADDRESS_UNION` estructura está establecida en `ADDRESS_KIND_ARRAYELEM` (un valor de la [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md) enumeración).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS_KIND](../../../extensibility/debugger/reference/address-kind.md)
