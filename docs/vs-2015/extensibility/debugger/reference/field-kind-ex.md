---
title: FIELD_KIND_EX | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- FIELD_KIND_EX enumeration
ms.assetid: 922c3208-1e94-485f-b70a-3bc96affeff8
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e6384ea963fe1da145cacc0be46b5989f7bc610
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58995857"
---
# <a name="fieldkindex"></a>FIELD_KIND_EX
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Enumera los tipos de campos adicionales que un [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) puede contener el objeto. Esta enumeración se extiende el [FIELD_KIND](../../../extensibility/debugger/reference/field-kind.md) enumeración.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
} ;  
typedef DWORD FIELD_KIND_EX;  
```  
  
```csharp  
public enum enum_FIELD_KIND_EX  
{  
   FIELD_KIND_EX_NONE = 0,  
   FIELD_TYPE_EX_METHODVAR = 0x1,  
   FIELD_TYPE_EX_CLASSVAR = 0x2  
};  
```  
  
## <a name="members"></a>Miembros  
 FIELD_KIND_EX_NONE  
 Campo no contiene un tipo extendido.  
  
 FIELD_TYPE_EX_METHODVAR  
 Campo contiene una variable de método.  
  
 FIELD_TYPE_EX_CLASSVAR  
 Campo contiene una variable de clase.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: Sh.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetExtendedKind](../../../extensibility/debugger/reference/idebugextendedfield-getextendedkind.md)
