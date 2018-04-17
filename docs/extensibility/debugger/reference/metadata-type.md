---
title: METADATA_TYPE | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 66a1632198a0af5490e66a843458fc55bcad2d6d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="metadatatype"></a>METADATA_TYPE
Esta estructura especifica información sobre un tipo de campo que se toman de metadatos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagTYPE_METADATA {  
   ULONG32  ulAppDomainID;  
   GUID     guidModule;  
   _mdToken tokClass;  
} METADATA_TYPE;  
```  
  
```csharp  
public struct METADATA_TYPE {  
   public uint ulAppDomainID;  
   public Guid guidModule;  
   public int  tokClass;  
};  
```  
  
#### <a name="parameters"></a>Parámetros  
 ulAppDomainID  
 Identificador de la aplicación del que procede el símbolo. Esto se utiliza para identificar de forma exclusiva una instancia de la aplicación.  
  
 guidModule  
 El GUID del módulo que contiene este campo.  
  
 tokClass  
 El identificador del token de metadatos de este tipo.  
  
 [C++] `_mdToken` es un `typedef` de 32 bits `int`.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura aparece como parte de la unión en el [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructura cuando la `dwKind` campo de la `TYPE_INFO` estructura está establecida en `TYPE_KIND_METADATA` (un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración).  
  
 El `tokClass` valor es un símbolo (token) de metadatos que identifica de forma única un tipo. Para obtener más información sobre cómo interpretar los bits superiores del identificador de token de metadatos, consulte la `CorTokenType` en el archivo corhdr.h en la enumeración de la [!INCLUDE[dnprdnshort](../../../code-quality/includes/dnprdnshort_md.md)] SDK.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)