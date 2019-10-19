---
title: 'Iscriptnode (:: Alive | Microsoft Docs'
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
ms.openlocfilehash: b7e0216824506ee942b42a42d5c3c4475f63f9e2
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573624"
---
# <a name="iscriptnodealive"></a>IScriptNode::Alive
Indica si un objeto todavía está activo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Alive();  
```  
  
#### <a name="parameters"></a>Parámetros  
 El método no toma ningún parámetro.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El nodo de script sigue estando activo.|  
  
## <a name="remarks"></a>Comentarios  
 Si el objeto no está activo, el modelo de objetos componentes (COM) devuelve un error del proxy de serialización para las llamadas a este método.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)