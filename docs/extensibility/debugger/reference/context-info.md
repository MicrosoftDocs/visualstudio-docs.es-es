---
title: CONTEXT_INFO | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CONTEXT_INFO
helpviewer_keywords:
- CONTEXT_INFO structure
ms.assetid: 6b513f4e-e7b0-4969-adf0-2205ccc1e09b
caps.latest.revision: 11
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
ms.openlocfilehash: 5cee396c4659807ca4dcded60f4d1f1fbbcc3f82
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---
# <a name="contextinfo"></a>CONTEXT_INFO
Esta estructura describe un contexto de la memoria o el contexto del código.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _tagCONTEXT_INFO {   
   CONTEXT_INFO_FIELDS dwFields;  
   BSTR                bstrModuleUrl;  
   BSTR                bstrFunction;  
   TEXT_POSITION       posFunctionOffset;  
   BSTR                bstrAddress;  
   BSTR                bstrAddressOffset;  
   BSTR                bstrAddressAbsolute;  
} CONTEXT_INFO;  
```  
  
```csharp  
public struct CONTEXT_INFO {  
   public uint          dwFields;  
   public string        bstrModuleUrl;  
   public string        bstrFunction;  
   public TEXT_POSITION posFunctionOffset;  
   public string        bstrAddress;  
   public string        bstrAddressOffset;  
   public string        bstrAddressAbsolute;  
};  
```  
  
## <a name="members"></a>Miembros  
 dwFields  
 Una combinación de marcas de él [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md) enumeración que especifica qué campos se rellenan**.**  
  
 bstrModuleUrl  
 El nombre del módulo donde se encuentra el contexto.  
  
 bstrFunction  
 El nombre de la función donde se encuentra el contexto.  
  
 posFunctionOffset  
 A [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) estructura que identifica el desplazamiento de línea y columna de la función asociada al contexto del código.  
  
 bstrAddress  
 La dirección en el código donde se encuentra el contexto determinado.  
  
 bstrAddressOffset  
 El desplazamiento de la dirección en el código donde se encuentra el contexto determinado.  
  
 bstrAddressAbsolute  
 La dirección absoluta en memoria donde se encuentra el contexto determinado.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se devuelve de una llamada a la [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md) método.  
  
 Un uso típico de esta estructura es como soporte de un **memoria** ventana de depuración.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmemorycontext2-getinfo.md)   
 [CONTEXT_INFO_FIELDS](../../../extensibility/debugger/reference/context-info-fields.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)
