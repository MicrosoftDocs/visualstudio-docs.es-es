---
title: MESSAGETYPE | Documentos de Microsoft
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
- MESSAGETYPE
helpviewer_keywords:
- MESSAGETYPE enumeration
ms.assetid: 800cc77d-3c27-4763-a9df-552a9384bd49
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: dc81ac400ce2a94674a97d9b987bf1a3e7843105
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49845446"
---
# <a name="messagetype"></a>MESSAGETYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica el tipo de mensaje y el motivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
typedef DWORD MESSAGETYPE;  
```  
  
```csharp  
public enum enum_MESSAGETYPE {   
   MT_OUTPUTSTRING      = 0x0000001,  
   MT_MESSAGEBOX        = 0x00000002,  
   MT_TYPE_MASK         = 0x000000FF,  
   MT_REASON_EXCEPTION  = 0x00000100,  
   MT_REASON_TRACEPOINT = 0x00000200,  
   MT_REASON_MASK       = 0x0000FF00  
};  
```  
  
## <a name="members"></a>Miembros  
 MT_OUTPUTSTRING  
 Indica que debe enviarse el mensaje a la ventana de salida. Es mutuamente excluyente de `MT_MESSAGEBOX`.  
  
 MT_MESSAGEBOX  
 Indica que debe mostrarse el mensaje en un cuadro de mensaje. Es mutuamente excluyente de `MT_OUTPUTSTRING`.  
  
 MT_TYPE_MASK  
 Un valor de máscara para aislar el destino del mensaje.  
  
 MT_REASON_EXCEPTION  
 Indica que se está mostrando un cuadro de mensaje como resultado una excepción. Es mutuamente excluyente de `MT_REASON_TRACEPOINT`.  
  
 MT_REASON_TRACEPOINT  
 Indica que se está mostrando un cuadro de mensaje como resultado de alcanzar un punto de seguimiento. Esto es mutuamente excluyente `MT_REASON_EXCEPTION`.  
  
 MT_REASON_MASK  
 Un valor de máscara para aislar el motivo del mensaje se muestra.  
  
## <a name="remarks"></a>Comentarios  
 Estos valores se devuelven desde el [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md) y [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md) métodos.  
  
 Uno de los valores de la razón puede combinarse con uno de los valores de destino de salida con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [GetMessage](../../../extensibility/debugger/reference/idebugmessageevent2-getmessage.md)   
 [GetErrorMessage](../../../extensibility/debugger/reference/idebugerrorevent2-geterrormessage.md)

