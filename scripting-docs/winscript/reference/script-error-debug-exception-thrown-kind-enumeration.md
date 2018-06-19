---
title: Enumeración SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: b3aa4966-e110-4b30-b368-1281a9740dbd
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6fe5b308ea75956d9e5826b4daadaef3a823141f
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734155"
---
# <a name="scripterrordebugexceptionthrownkind-enumeration"></a>Enumeración SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND
Indica la clase de la excepción producida. Esta enumeración se usa en la [IActiveScriptErrorDebug110::GetExceptionThrownKind](../../winscript/reference/iactivescripterrordebug110-getexceptionthrownkind.md) método.  
  
> [!IMPORTANT]
>  Estas constantes se implementan mediante PDM versión 11.0 y versiones posteriores. Se encuentra en activdbg100.h.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
typedef SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND  
```  
  
## <a name="members"></a>Miembros  
  
|Miembro|Valor|Descripción|  
|------------|-----------|-----------------|  
|ETK_FIRST_CHANCE|0x00000000|La excepción es una excepción de primera aparición.|  
|ETK_USER_UNHANDLED|0x00000001|La excepción no se controla en el código de usuario.|  
|ETK_UNHANDLED|0x00000002|La excepción no se controla en el código.|  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptErrorDebug110 (Interfaz)](../../winscript/reference/iactivescripterrordebug110-interface.md)