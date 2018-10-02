---
title: REFERENCE_TYPE | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- REFERENCE_TYPE
helpviewer_keywords:
- REFERENCE_TYPE enumeration
ms.assetid: b1ffba10-eb9d-48ba-bf48-6d8b71d6f270
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8cf76615deec5ef8368d38f7bc47451764cf33e9
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577184"
---
# <a name="referencetype"></a>REFERENCE_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [REFERENCE_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/reference-type).  
  
Especifica el tipo de referencia.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
typedef DWORD REFERENCE_TYPE;  
```  
  
```csharp  
public enum enum_REFERENCE_TYPE {   
   REF_TYPE_WEAK   = 0x0001,  
   REF_TYPE_STRONG = 0x0002  
};  
```  
  
## <a name="members"></a>Miembros  
 REF_TYPE_WEAK  
 Especifica una referencia débil. No se puede combinar con `REF_TYPE_STRONG`.  
  
 REF_TYPE_STRONG  
 Especifica una referencia segura. No se puede combinar con `REF_TYPE_WEAK`.  
  
## <a name="remarks"></a>Comentarios  
 Usar como el `dwRefType` miembro de la [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) estructura.  
  
 Pasado como parámetro a la [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)   
 [SetReferenceType](../../../extensibility/debugger/reference/idebugreference2-setreferencetype.md)

