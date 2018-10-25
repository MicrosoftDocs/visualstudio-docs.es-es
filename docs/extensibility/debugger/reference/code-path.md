---
title: CODE_PATH | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- CODE_PATH
helpviewer_keywords:
- CODE_PATH structure
ms.assetid: 2d4b2890-4c9d-47e1-83c0-df9c6436427f
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: a9618d28aeadaa85d97e9018fdf57ee8952ac3fd
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49920266"
---
# <a name="codepath"></a>CODE_PATH
Describe una llamada de método o función.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct tagCODE_PATH {   
   BSTR                bstrName;  
   IDebugCodeContext2* pCode;  
} CODE_PATH;  
```  
  
```csharp  
public struct CODE_PATH {  
   public string            bstrName;  
   public IDebugCodeContext pCode;  
}  
```  
  
## <a name="members"></a>Miembros  
 bstrName  
 El nombre de la ruta de acceso del código.  
  
 pCode  
 El [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) objeto que identifica donde se encuentra en el código paso a paso una función.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se usa para implementar la ejecución paso a paso en una función. [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md) devuelve todas las llamadas desde la ubicación actual en el programa que se está depurando. Esta estructura representa una de estas llamadas.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [EnumCodePaths](../../../extensibility/debugger/reference/idebugprogram2-enumcodepaths.md)