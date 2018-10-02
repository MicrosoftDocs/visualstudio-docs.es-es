---
title: dwTYPE_KIND | Microsoft Docs
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
- dwTYPE_KIND
helpviewer_keywords:
- dwTYPE_KIND enumeration
ms.assetid: 6ff56b0f-c502-4e6c-9829-bfa05361b783
caps.latest.revision: 9
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 026cf5e3f26cc6faeb8e8829295c0875203d88d1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47578928"
---
# <a name="dwtypekind"></a>dwTYPE_KIND
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [dwTYPE_KIND](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/dwtype-kind).  
  
Especifica cómo interpretar el tipo de un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
  
typedef DWORD dwTYPE_KIND;  
```  
  
```csharp  
public enum enum_dwTYPE_KIND {  
   TYPE_KIND_METADATA = 0x0001,  
   TYPE_KIND_PDB      = 0x0002,  
   TYPE_KIND_BUILT    = 0x0003,  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 TYPE_KIND_METADATA  
 El [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) union debe interpretarse como un [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) estructura.  
  
 TYPE_KIND_PDB  
 El `TYPE_INFO` union debe interpretarse como un [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) estructura.  
  
 TYPE_KIND_BUILT  
 El `TYPE_INFO` union debe interpretarse como un [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) estructura.  
  
## <a name="remarks"></a>Comentarios  
 Los valores de esta enumeración aparecen en la `dwKind` campo de la [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructurar y se usan para determinar cómo interpretar la `type` miembro de unión. El `TYPE_INFO` estructura devuelto por una llamada a la [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [GetTypeInfo](../../../extensibility/debugger/reference/idebugfield-gettypeinfo.md)   
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)   
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)   
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)

