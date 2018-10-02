---
title: OBJECT_TYPE | Documentos de Microsoft
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
- OBJECT_TYPE
helpviewer_keywords:
- OBJECT_TYPE enumeration
ms.assetid: c4d246f9-8a98-44ec-b2bb-ff5c684f668e
caps.latest.revision: 10
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 1cd02a49a92eefae129e53322b005760733e0417
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47568141"
---
# <a name="objecttype"></a>OBJECT_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [OBJECT_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/object-type).  
  
Especifica el tipo de un objeto desde el evaluador de expresiones.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
typedef DWORD OBJECT_TYPE;  
```  
  
```csharp  
public enum enum_OBJECT_TYPE {   
   OBJECT_TYPE_BOOLEAN = 0x0,  
   OBJECT_TYPE_CHAR    = 0x1,  
   OBJECT_TYPE_I1      = 0x2,  
   OBJECT_TYPE_U1      = 0x3,  
   OBJECT_TYPE_I2      = 0x4,  
   OBJECT_TYPE_U2      = 0x5,  
   OBJECT_TYPE_I4      = 0x6,  
   OBJECT_TYPE_U4      = 0x7,  
   OBJECT_TYPE_I8      = 0x8,  
   OBJECT_TYPE_U8      = 0x9,  
   OBJECT_TYPE_R4      = 0xa,  
   OBJECT_TYPE_R8      = 0xb,  
   OBJECT_TYPE_OBJECT  = 0xc,  
   OBJECT_TYPE_NULL    = 0xd,  
   OBJECT_TYPE_CLASS   = 0xe  
};  
```  
  
## <a name="members"></a>Miembros  
 OBJECT_TYPE_BOOLEAN  
 Indica que el objeto es un valor booleano.  
  
 OBJECT_TYPE_CHAR  
 Indica que el objeto es un carácter.  
  
 OBJECT_TYPE_I1  
 Indica que el objeto es un entero con signo de un byte.  
  
 OBJECT_TYPE_U1  
 Indica que el objeto es un entero sin signo de un byte.  
  
 OBJECT_TYPE_I2  
 Indica que el objeto es un entero con signo de dos bytes.  
  
 OBJECT_TYPE_U2  
 Indica que el objeto es un entero sin signo de dos bytes.  
  
 OBJECT_TYPE_I4  
 Indica que el objeto es un entero con signo de cuatro bytes.  
  
 OBJECT_TYPE_U4  
 Indica que el objeto es un entero sin signo de cuatro bytes.  
  
 OBJECT_TYPE_I8  
 Indica que el objeto es un entero con signo de ocho bytes.  
  
 OBJECT_TYPE_U8  
 Indica que el objeto es un entero sin signo de ocho bytes.  
  
 OBJECT_TYPE_R4  
 Indica que el objeto es un número de punto flotante de cuatro bytes.  
  
 OBJECT_TYPE_R8  
 Indica que el objeto es un número de punto flotante de ocho bytes.  
  
 OBJECT_TYPE_OBJECT  
 Indica que el objeto es un objeto.  
  
 OBJECT_TYPE_NULL  
 Indica que el objeto es NULL.  
  
 OBJECT_TYPE_CLASS  
 Indica que el objeto es una clase.  
  
## <a name="remarks"></a>Comentarios  
 Se pasa como argumento a la [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md) y [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md) métodos.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: ee.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [CreatePrimitiveObject](../../../extensibility/debugger/reference/idebugfunctionobject-createprimitiveobject.md)   
 [CreateArrayObject](../../../extensibility/debugger/reference/idebugfunctionobject-createarrayobject.md)

