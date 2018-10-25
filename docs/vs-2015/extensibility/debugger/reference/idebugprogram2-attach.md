---
title: IDebugProgram2::Attach | Documentos de Microsoft
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
- IDebugProgram2::Attach
helpviewer_keywords:
- IDebugProgram2::Attach
ms.assetid: de069fbf-a565-4905-b102-f5658c55aacd
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c64b4839d2f16adfcf40b082d54f60a95d7a468
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49881645"
---
# <a name="idebugprogram2attach"></a>IDebugProgram2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Se une al programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usará para la notificación de eventos de depuración.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra algunos posibles códigos de error.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El programa especificado ya está asociado al depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el procedimiento de conexión.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|No se puede adjuntar un programa de escritorio al depurador.|  
  
## <a name="remarks"></a>Comentarios  
 Un motor de depuración (DE) nunca llama a este método para asociar a un programa. Si la DE se ejecuta en el espacio de direcciones del programa, el [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) se llama al método. Si el espacio de direcciones de las ejecuciones DE en el Administrador de depuración de sesión (SDM) el [adjuntar](../../../extensibility/debugger/reference/idebugengine2-attach.md) se llama al método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [OnAttach](../../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [Asociar](../../../extensibility/debugger/reference/idebugengine2-attach.md)

