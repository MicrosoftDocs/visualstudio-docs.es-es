---
title: AD_PROCESS_ID_TYPE | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: d471a73205383f0f23c5016872712a3ba2c578d6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68153620"
---
# <a name="ad_process_id_type"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Especifica cómo interpretar un identificador de proceso en la estructura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp#  
enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
typedef DWORD AD_PROCESS_ID_TYPE;  
```  
  
```csharp  
public enum enum_AD_PROCESS_ID {  
   AD_PROCESS_ID_SYSTEM = 0,  
   AD_PROCESS_ID_GUID   = 1  
};  
```  
  
## <a name="members"></a>Miembros  
 AD_PROCESS_ID_SYSTEM  
 El identificador de proceso es un identificador de sistema. Utilice el `ProcessId.dwProcessId` campo de la estructura de [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) .  
  
 AD_PROCESS_ID_GUID  
 El ID. de proceso es un GUID. Use el `ProcessId.guidProcessId` campo de la `AD_PROCESS_ID` estructura.  
  
## <a name="remarks"></a>Observaciones  
 Se usa para el `ProcessIdType` miembro de la estructura [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) para identificar el tipo de identificador de proceso contenido en la estructura. Determina cómo se interpreta la `ProcessId` Unión en la estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg. h  
  
 Espacio de nombres: Microsoft. VisualStudio. Debugger. Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Consulte también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)
