---
title: 'Iactivescriptsitedebug:: Getrootapplicationnode | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSiteDebug.GetRootApplicationNode
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSiteDebug::GetRootApplicationNode
ms.assetid: 2393f566-6b97-47c0-8041-4dd7e3b1d3a3
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 40c837d5ee2e8b75bfe7603370d61385a67080cc
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54088522"
---
# <a name="iactivescriptsitedebuggetrootapplicationnode"></a>IActiveScriptSiteDebug::GetRootApplicationNode
Obtiene el nodo de la aplicación en qué secuencia de comandos se deben agregar documentos.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetRootApplicationNode(  
   IDebugApplicationNode**  ppdanRoot  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppdanRoot`  
 [out] El nodo de la aplicación de depuración que contiene los documentos de script. Puede ser `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve el nodo de la aplicación en la que se deben agregar a documentos de script. El método puede devolver `NULL` para `ppdanRoot` si los documentos de script deben ser de nivel superior.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSiteDebug (Interfaz)](../../winscript/reference/iactivescriptsitedebug-interface.md)