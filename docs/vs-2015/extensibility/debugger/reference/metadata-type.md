---
title: METADATA_TYPE | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 8e8b5cc4c0a067a8add062d2003e991eb8672af5
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51732156"
---
# <a name="metadatatype"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta estructura especifica información sobre un tipo de campo que se toman de los metadatos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
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
 El identificador de token de metadatos de este tipo.  
  
 [C++] `_mdToken` es un `typedef` para 32 bits `int`.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura aparece como parte de la unión en el [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) estructura cuando la `dwKind` campo de la `TYPE_INFO` estructura está establecida en `TYPE_KIND_METADATA` (un valor de la [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) enumeración).  
  
 El `tokClass` valor es un token de metadatos que identifica un tipo. Para obtener más información sobre cómo interpretar los bits superiores del identificador del token de metadatos, vea el `CorTokenType` enumeración en el archivo corhdr.h el [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)

