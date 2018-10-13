---
title: IDebugProgramEx2::Attach | Documentos de Microsoft
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
- IDebugProgramEx2::Attach
helpviewer_keywords:
- IDebugProgramEx2::Attach
ms.assetid: 33b22b2f-431e-4205-9441-d28a9c928c97
caps.latest.revision: 14
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 894cc3bf9ccc5104d5767186a141349941a708a2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49294338"
---
# <a name="idebugprogramex2attach"></a>IDebugProgramEx2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Asociar una sesión de un programa.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   DWORD                 dwReason,  
   IDebugSession2*       pSession  
);  
```  
  
```  
[C#]  
int Attach(   
   IDebugEventCallback2 pCallback,  
   uint                 dwReason,  
   IDebugSession2       pSession  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pCallback`  
 [in] Un [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) objeto que representa la función de devolución de llamada que el motor de depuración adjuntos envía eventos a.  
  
 `dwReason`  
 [in] Un valor de la [ATTACH_REASON](../../../extensibility/debugger/reference/attach-reason.md) enumeración que describe el motivo de la operación de adjuntar.  
  
 `pSession`  
 [in] Un valor que identifica de forma única la sesión que se está asociando al programa.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. Este método debe devolver `E_ATTACH_DEBUGGER_ALREADY_ATTACHED` si el programa ya está asociado.  
  
## <a name="remarks"></a>Comentarios  
 El puerto que contiene el programa puede usar el valor de `pSession` para determinar qué sesión está intentando adjuntar al programa. Por ejemplo, si un puerto permite la sesión de solo depuración adjuntar a un proceso a la vez, el puerto puede determinar si la misma sesión ya está conectada a otros programas en el proceso.  
  
> [!NOTE]
>  La interfaz pasa `pSession` se trata solo como una cookie, un valor que identifica el Administrador de depuración de la sesión asociar a este programa; ninguno de los métodos en la interfaz proporcionado son funcional.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)

