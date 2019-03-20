---
title: IActiveScriptSiteDebug::GetRootApplicationNode | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 18e603289931115bcaac4d6bb7707b7886f506d4
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58148274"
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