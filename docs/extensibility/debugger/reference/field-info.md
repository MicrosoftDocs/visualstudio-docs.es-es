---
title: FIELD_INFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: FIELD_INFO
helpviewer_keywords: FIELD_INFO structure
ms.assetid: bfafef6d-0c83-43d7-a779-1f0d24b166a1
caps.latest.revision: "14"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 5b7b3bfae3923a7df3f5c499bfac5cde12d1388b
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="fieldinfo"></a>FIELD_INFO
Esta estructura describe una variable local, parámetro u otro campo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagFieldInfo {   
   FIELD_INFO_FIELDS dwFields;  
   BSTR              bstrFullName;  
   BSTR              bstrName;  
   BSTR              bstrType;  
   FIELD_MODIFIERS   dwModifiers;  
} FIELD_INFO;  
```  
  
```csharp  
public struct FIELD_INFO {  
   public uint   dwFields;  
   public string bstrFullName;  
   public string bstrName;  
   public string bstrType;  
   public uint   dwModifiers;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwFields  
 Una combinación de indicadores de la [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md) enumeración que especifica qué miembros se rellenan.  
  
 bstrFullName  
 El nombre completo del campo.  
  
 bstrName  
 El nombre corto del campo.  
  
 bstrType parámetro  
 El tipo del campo.  
  
 dwModifiers  
 Una combinación de indicadores de la [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md) enumeración que describe el campo.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md) método donde se rellena.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [FIELD_INFO_FIELDS](../../../extensibility/debugger/reference/field-info-fields.md)   
 [FIELD_MODIFIERS](../../../extensibility/debugger/reference/field-modifiers.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugfield-getinfo.md)