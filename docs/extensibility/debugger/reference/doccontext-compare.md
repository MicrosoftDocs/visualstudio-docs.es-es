---
title: DOCCONTEXT_COMPARE | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 10
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
ms.openlocfilehash: 77c810bb6e4791fbc0c3cf787f340a8d996ce037
ms.contentlocale: es-es
ms.lasthandoff: 09/26/2017

---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
Especifica los criterios para comparar dos contextos de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
```  
  
## <a name="members"></a>Miembros  
 DOCCONTEXT_EQUAL  
 Busque el primer contexto del documento en la lista que es igual que el contexto del documento de destino.  
  
 DOCCONTEXT_LESS_THAN  
 Busque el primer contexto del documento en la lista que es menor que el contexto del documento de destino.  
  
 DOCCONTEXT_GREATER_THAN  
 Busque el primer contexto del documento en la lista que es mayor que el contexto del documento de destino.  
  
 DOCCONTEXT_SAME_DOCUMENT  
 Busque el primer contexto del documento en la lista que se encuentra en el mismo documento que el contexto del documento de destino.  
  
## <a name="remarks"></a>Comentarios  
 Pasa como un argumento a la [comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) método.  
  
 Estos valores se utilizan para especificar un criterio de comparación para buscar el primer contexto del documento en una lista. Un contexto de documento se proporciona una lista de contextos de documento compararse a sí mismo con respecto a través de la `IDebugDocumentContext2::Compare` método. El primer contexto del documento en la lista para que el operador de comparación es `true` , a continuación, se devuelve.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)
