---
title: CONSTRUCTOR_ENUM | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CONSTRUCTOR_ENUM
helpviewer_keywords: CONSTRUCTOR_ENUM enumeration
ms.assetid: 6d335b2c-66bc-460c-a4a6-4f3f1b697c2c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 939c41443bbd80dff2531591728d0a75536a982d
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="constructorenum"></a>CONSTRUCTOR_ENUM
Selecciona distintos tipos de constructores.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
} CONSTRUCTOR_ENUM;  
```  
  
```csharp  
public enum ConstructorMatchOptions {   
   crAll       = 0,  
   crNonStatic = 1,  
   crStatic    = 2  
};  
```  
  
## <a name="members"></a>Miembros  
 crAll  
 Selecciona todos los constructores.  
  
 crNonStatic  
 Selecciona los constructores no estáticos.  
  
 crStatic  
 Selecciona los constructores estáticos.  
  
## <a name="remarks"></a>Comentarios  
 Pasa como un argumento a la [EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetReason](../../../extensibility/debugger/reference/idebugcanstopevent2-getreason.md)