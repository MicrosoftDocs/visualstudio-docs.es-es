---
title: IApplicationDebugger::QueryAlive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IApplicationDebugger.QueryAlive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IApplicationDebugger::QueryAlive
ms.assetid: 41181ebb-a3bf-4e41-82af-d6c7348dc706
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6b4c455305116863a4a8ad16ff21cd7554a36239
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147701"
---
# <a name="iapplicationdebuggerqueryalive"></a>IApplicationDebugger::QueryAlive
Indica si el depurador está respondiendo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 Este método indica si el depurador está respondiendo. Las implementaciones de este método siempre deben devolver `S_OK`.  
  
 Si el proceso del depurador finaliza inesperadamente, COM devuelve un error desde el proxy de cálculo de referencias para las llamadas a este método.  
  
## <a name="see-also"></a>Vea también  
 [IApplicationDebugger (Interfaz)](../../winscript/reference/iapplicationdebugger-interface.md)