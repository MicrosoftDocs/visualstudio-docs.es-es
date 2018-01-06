---
title: IDebugProcess2::Attach | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProcess2::Attach
helpviewer_keywords: IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 47b14c3de6b5b9980e2ad420596a1243e84c8882
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
El Administrador de sesión de depuración (SDM) se asocia al proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que se usa para la notificación de eventos de depuración.  
  
 `rgguidSpecificEngines`  
 [in] Una matriz de GUID de motores de depuración que se va a usar para depurar programas que se ejecutan en el proceso. Este parámetro puede ser un valor null. Para obtener más información, vea la sección Comentarios.  
  
 `celtSpecificEngines`  
 [in] El número de depuración motores en el `rgguidSpecificEngines` matriz y el tamaño de la `rghrEngineAttach` matriz.  
  
 `rghrEngineAttach`  
 [entrada, salida] Una matriz de códigos HRESULT devuelto por los motores de depuración. El tamaño de esta matriz se especifica en el `celtSpecificEngines` parámetro. Cada código sea normalmente `S_OK` o `S_ATTACH_DEFERRED`. Estos últimos indican que la DE está actualmente conectada a ningún programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se realiza correctamente, devuelve `S_OK`; en caso contrario, devuelve un código de error. La tabla siguiente muestran otros valores posibles.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|El proceso especificado ya está asociado al depurador.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|Se ha producido una infracción de seguridad durante el proceso de adjuntar.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Un proceso de escritorio no se puede adjuntar el depurador.|  
  
## <a name="remarks"></a>Comentarios  
 Adjuntar a un proceso asocia el SDM en todos los programas que se ejecutan en ese proceso que se puede depurar mediante los motores de depuración (Alemania) especificados en el `rgguidSpecificEngines` matriz. Establecer el `rgguidSpecificEngines` parámetro en un valor null de valor o incluir `GUID_NULL` en la matriz para adjuntar a todos los programas en el proceso.  
  
 Todos los eventos de depuración que se producen en el proceso se envían a la determinada [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto. Esto `IDebugEventCallback2` se proporciona el objeto cuando el SDM llama a este método.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)