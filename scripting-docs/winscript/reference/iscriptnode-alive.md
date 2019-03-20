---
title: IScriptNode::Alive | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.Alive
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::Alive
ms.assetid: d2755c83-e9b9-4c0a-acb7-25b554fc9fe8
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: da0a55d26b5ab643670ba7ed51e576eeb89d8b98
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159223"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indica si un objeto aún está activo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parámetros  
 El método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El nodo de secuencia de comandos todavía está activo.|  
  
## <a name="remarks"></a>Comentarios  
 Si el objeto no está activo, el modelo de objetos componentes (COM) devuelve un error desde el proxy de cálculo de referencias para las llamadas a este método.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)