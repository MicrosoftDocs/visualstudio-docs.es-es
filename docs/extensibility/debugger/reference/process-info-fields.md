---
title: PROCESS_INFO_FIELDS | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- PROCESS_INFO_FIELDS
helpviewer_keywords:
- PROCESS_INFO_FIELDS enumeration
ms.assetid: 0d9cc345-3d3a-44d8-ae15-a67acb97a828
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 3376db379e4e911bcaa8e865a16c63d1251229f6
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
ms.locfileid: "31126391"
---
# <a name="processinfofields"></a>PROCESS_INFO_FIELDS
Especifica qué tipo de información que se va a recuperar de un proceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
typedef DWORD PROCESS_INFO_FIELDS;  
```  
  
```csharp  
public enum enum_PROCESS_INFO_FIELDS {   
   PIF_FILE_NAME             = 0x00000001,  
   PIF_BASE_NAME             = 0x00000002,  
   PIF_TITLE                 = 0x00000004,  
   PIF_PROCESS_ID            = 0x00000008,  
   PIF_SESSION_ID            = 0x00000010,  
   PIF_ATTACHED_SESSION_NAME = 0x00000020,  
   PIF_CREATION_TIME         = 0x00000040,  
   PIF_FLAGS                 = 0x00000080,  
   PIF_ALL                   = 0x000000ff  
};  
```  
  
## <a name="members"></a>Miembros  
 PIF_FILE_NAME  
 Inicializar o utilizar el `bstrFileName` campo de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura.  
  
 PIF_BASE_NAME  
 Inicializar o utilizar el `bstrBaseName` campo de la `PROCESS_INFO` estructura.  
  
 PIF_TITLE  
 Inicializar o utilizar el `bstrTitle` campo de la `PROCESS_INFO` estructura.  
  
 PIF_PROCESS_ID  
 Inicializar o utilizar el `ProcessId` campo de la `PROCESS_INFO` estructura.  
  
 PIF_SESSION_ID  
 Inicializar o utilizar el `dwSessionId` campo de la `PROCESS_INFO` estructura.  
  
 PIF_ATTACHED_SESSION_NAME  
 Inicializar o utilizar el `bstrAttachedSessionName` campo de la `PROCESS_INFO` estructura.  
  
 PIF_CREATION_TIME  
 Inicializar o utilizar el `CreationTime` campo de la `PROCESS_INFO` estructura.  
  
 PIF_FLAGS  
 Inicializar o utilizar el `Flags` campo de la `PROCESS_INFO` estructura.  
  
 PIF_ALL  
 Rellena todos los campos.  
  
## <a name="remarks"></a>Comentarios  
 Pasa a la [GetInfo](../../../extensibility/debugger/reference/idebugprocess2-getinfo.md) método para indicar qué campos de la [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) estructura deben inicializarse.  
  
 También se utiliza en `Fields` campo de la `PROCESS_INFO` estructura para indicar qué campos se utilizan y válido.  
  
 Estas marcas se pueden combinar con un bit a bit `OR`.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)