---
title: DOCCONTEXT_COMPARE | Microsoft Docs
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
- DOCCONTEXT_COMPARE
helpviewer_keywords:
- DOCCONTEXT_COMPARE enumeration
ms.assetid: ed947c34-b07e-4b69-8381-b6e7cb842862
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 0598fd3848623bdbef39f0c1cfec145399fbdc04
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51758167"
---
# <a name="doccontextcompare"></a>DOCCONTEXT_COMPARE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica los criterios para comparar dos contextos de documento.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_DOCCONTEXT_COMPARE {   
   DOCCONTEXT_EQUAL         = 0x0001,  
   DOCCONTEXT_LESS_THAN     = 0x0002,  
   DOCCONTEXT_GREATER_THAN  = 0x0003,  
   DOCCONTEXT_SAME_DOCUMENT = 0x0004  
};  
typedef DWORD DOCCONTEXT_COMPARE;  
```  
  
```csharp  
enum enum_DOCCONTEXT_COMPARE {   
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
 Se pasa como argumento a la [comparar](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md) método.  
  
 Estos valores se utilizan para especificar un criterio de comparación para encontrar el primer contexto del documento en una lista. Un contexto de documento se proporciona una lista de contextos de documento para comparar propio frente a través de la `IDebugDocumentContext2::Compare` método. El primer contexto de documento en la lista para que el operador de comparación es `true` , a continuación, se devuelve.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [Compare](../../../extensibility/debugger/reference/idebugdocumentcontext2-compare.md)

