---
title: IMachineDebugManagerCookie::EnumApplications | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IMachineDebugManagerCookie.EnumApplications
apilocation:
- scrobj.dll
helpviewer_keywords:
- IMachineDebugManagerCookie::EnumApplications
ms.assetid: 03f863cf-fa7f-4ec4-b1a1-1ae0ad296c39
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 927457fca1972148798b543dceefa19e107f45d6
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="imachinedebugmanagercookieenumapplications"></a>IMachineDebugManagerCookie::EnumApplications
Devuelve un enumerador de la lista actual de las aplicaciones en ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumApplications(  
   IEnumRemoteDebugApplications**  ppeda  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppeda`  
 [out] Enumerador que contiene la lista actual de las aplicaciones en ejecución.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un enumerador de la lista actual de las aplicaciones en ejecución. El depurador IDE utiliza este método para mostrar y conectar las aplicaciones para fines de depuración.  
  
## <a name="see-also"></a>Vea también  
 [IMachineDebugManagerCookie (Interfaz)](../../winscript/reference/imachinedebugmanagercookie-interface.md)