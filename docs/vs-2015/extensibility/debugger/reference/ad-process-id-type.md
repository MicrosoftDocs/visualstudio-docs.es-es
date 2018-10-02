---
title: AD_PROCESS_ID_TYPE | Documentos de Microsoft
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
- AD_PROCESS_ID_TYPE
helpviewer_keywords:
- AD_PROCESS_ID_TYPE enumeration
ms.assetid: 0aab80e9-285a-4697-94ac-c864d42a6aaa
caps.latest.revision: 7
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 4c9327c84b8cdac8eab1a00b7dd2b665456dcaaa
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47575550"
---
# <a name="adprocessidtype"></a>AD_PROCESS_ID_TYPE
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [AD_PROCESS_ID_TYPE](https://docs.microsoft.com/visualstudio/extensibility/debugger/reference/ad-process-id-type).  
  
Especifica cómo interpretar un identificador de proceso en el [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estructura.  
  
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
 Id. de proceso es un identificador de sistema. Use la `ProcessId.dwProcessId` campo de la [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estructura.  
  
 AD_PROCESS_ID_GUID  
 Id. de proceso es un GUID. Use la `ProcessId.guidProcessId` campo de la `AD_PROCESS_ID` estructura.  
  
## <a name="remarks"></a>Comentarios  
 Utilizado para la `ProcessIdType` miembro de la [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) estructura para identificar el tipo de identificador de proceso que se encuentra en la estructura. Determina cómo se interpretan los `ProcessId` union en la estructura.  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Enumeraciones](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)

