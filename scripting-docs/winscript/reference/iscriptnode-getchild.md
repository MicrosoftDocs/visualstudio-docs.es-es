---
title: IScriptNode::GetChild | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.GetChild
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::GetChild
ms.assetid: 8cb3f8b0-958b-40bb-a91a-49a788661861
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: d127b1b8a8db0c6d272e50d33b523fbe182a9e21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24734225"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Devuelve al elemento secundario que está en el índice especificado en el nodo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `isn`  
 [in] El índice del elemento secundario en el elemento primario.  
  
 `ppsn`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptNode` interfaz de la instancia secundaria.  
  
 Para `IScriptNode` objetos que representan una página Web, este parámetro devuelve un objeto que contiene un bloque de script.  
  
 Para `IScriptEntry` objetos que especifican un bloque de script, este parámetro devuelve un objeto que especifica una función.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Para `IScriptEntry` objetos que especifican un objeto de función y para `IScriptScriptlet` objetos, este método produce un error porque no hay entradas secundarias.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)