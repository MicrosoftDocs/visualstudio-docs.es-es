---
title: METADATA_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- METADATA_TYPE
helpviewer_keywords:
- METADATA_TYPE structure
ms.assetid: 2d8b78f6-0aef-4d79-809a-cff9b2c24659
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1be7cb6071a0307a56285b8929e52e038c263fdc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "62546829"
---
# <a name="metadata_type"></a>METADATA_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Esta estructura especifica información sobre un tipo de campo tomado de los metadatos.  
  
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
 IDENTIFICADOR de la aplicación de la que procede el símbolo. Se utiliza para identificar de forma única una instancia de la aplicación.  
  
 guidModule  
 GUID del módulo que contiene este campo.  
  
 tokClass  
 IDENTIFICADOR del token de metadatos de este tipo.  
  
 [C++] `_mdToken` es un `typedef` para un 32 bits `int` .  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura aparece como parte de la Unión en la estructura [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) cuando el `dwKind` campo de la `TYPE_INFO` estructura se establece en `TYPE_KIND_METADATA` (un valor de la enumeración [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md) ).  
  
 El `tokClass` valor es un token de metadatos que identifica un tipo de forma única. Para obtener más información sobre cómo interpretar los bits superiores del identificador del token de metadatos, consulte la `CorTokenType` enumeración en el archivo CorHdr. h en el [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] SDK.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: SH. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)   
 [dwTYPE_KIND](../../../extensibility/debugger/reference/dwtype-kind.md)
