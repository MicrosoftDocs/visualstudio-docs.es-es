---
title: IRemoteDebugApplication::QueryAlive | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IRemoteDebugApplication.QueryAlive
apilocation: pdm.dll
helpviewer_keywords: IRemoteDebugApplication::QueryAlive
ms.assetid: 08e49d3b-6fb3-4438-960e-f05395ba9b17
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3f938ad30562cd1131e8a50077106002d33cea2b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iremotedebugapplicationqueryalive"></a>IRemoteDebugApplication::QueryAlive
Indica si la aplicación está respondiendo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT QueryAlive();  
```  
  
#### <a name="parameters"></a>Parámetros  
 Este método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método indica si la aplicación está respondiendo. Las implementaciones de este método siempre deben devolver `S_OK`.  
  
 Si el proceso de la aplicación termina de forma inesperada, COM devuelve un error en el proxy de cálculo de referencias para las llamadas a este método.  
  
## <a name="see-also"></a>Vea también  
 [IRemoteDebugApplication (Interfaz)](../../winscript/reference/iremotedebugapplication-interface.md)