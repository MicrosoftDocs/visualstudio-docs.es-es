---
title: BP_LOCATION_CODE_STRING | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- BP_LOCATION_CODE_STRING
helpviewer_keywords:
- BP_LOCATION_CODE_STRING structure
ms.assetid: a4cd71c6-5052-45fe-907b-ebc6ca1df2e4
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 50c48098aee3b1077edec99210e7ab624d2a8d6c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153461"
---
# <a name="bp_location_code_string"></a>BP_LOCATION_CODE_STRING
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Se usa para establecer puntos de interrupción de código basados en una cadena que el usuario puede especificar desde el entorno de desarrollo integrado (IDE).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
typedef struct _BP_LOCATION_CODE_STRING {   
   BSTR bstrContext;  
   BSTR bstrCodeExpr;  
} BP_LOCATION_CODE_STRING;  
```  
  
## <a name="members"></a>Miembros  
 `bstrContext`  
 Contexto del punto de interrupción en el código, normalmente un nombre de método o función tal y como se ha detectado en una pila de llamadas.  
  
 `bstrCodeExpr`  
 Cadena en la que el usuario escribe para describir el punto de interrupción de código.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura es miembro de la estructura [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) como parte de una Unión.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)
