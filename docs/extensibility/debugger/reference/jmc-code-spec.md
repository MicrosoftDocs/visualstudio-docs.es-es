---
title: JMC_CODE_SPEC | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: JMC_CODE_SPEC
helpviewer_keywords: JMC_CODE_SPEC structure
ms.assetid: d89498f1-4234-46d9-b4e2-abbcbca5068a
caps.latest.revision: "6"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 2bfcd1f63196856eef7fa7293d9efbc07c9813a9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="jmccodespec"></a>JMC_CODE_SPEC
Esta estructura se usa para establecer la información de JustMyCode de un módulo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
typedef struct _JMC_CODE_SPEC {  
   BOOL fIsUserCode;  
   BSTR bstrModuleName;  
} JMC_CODE_SPEC;  
```  
  
```csharp  
public struct JMC_CODE_SPEC {  
   public int    fIsUserCode;  
   public string bstrModuleName;  
};  
```  
  
## <a name="members"></a>Miembros  
 fIsUserCode  
 Es distinto de cero (`TRUE`) si el módulo es deben considerarse código de usuario; en caso contrario, es cero (`FALSE`) si el módulo se tratará como código externo y no va a depurar.  
  
 bstrModuleName  
 Nombre del módulo en cuestión.  
  
## <a name="remarks"></a>Comentarios  
 Esta estructura se pasa como una lista de estas estructuras para la [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Estructuras y uniones](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [SetJustMyCodeState](../../../extensibility/debugger/reference/idebugengine3-setjustmycodestate.md)