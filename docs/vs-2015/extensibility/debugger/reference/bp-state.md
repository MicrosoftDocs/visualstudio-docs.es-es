---
title: BP_STATE | Microsoft Docs
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
- BP_STATE
helpviewer_keywords:
- BP_STATE enumeration
ms.assetid: 08aa6a3f-3e5f-4c83-8eca-7b7b5f8e208d
caps.latest.revision: 11
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: f6fc9cdcdedb9b733da27489232558f394879cc1
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47581275"
---
# <a name="bpstate"></a>BP_STATE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [BP_STATE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/bp-state).  
  
Especifica la existencia de un punto de interrupción enlazado y también especifica si está habilitado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
typedef DWORD BP_STATE;  
```  
  
```csharp  
public enum enum_BP_STATE {   
   BPS_NONE     = 0x0000,  
   BPS_DELETED  = 0x0001,  
   BPS_DISABLED = 0x0002,  
   BPS_ENABLED  = 0x0003  
};  
```  
  
## <a name="members"></a>Miembros  
 BPS_NONE  
 Especifica que no existe ningún punto de interrupción.  
  
 BPS_DELETED  
 Especifica que se ha eliminado el punto de interrupción.  
  
 BPS_DISABLED  
 Especifica que el punto de interrupción está deshabilitado.  
  
 BPS_ENABLED  
 Especifica que el punto de interrupción está habilitado.  
  
## <a name="remarks"></a>Comentarios  
 Devuelve el [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md) método.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetState](../../../extensibility/debugger/reference/idebugboundbreakpoint2-getstate.md)

