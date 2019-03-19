---
title: IScriptNode::GetChild | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 78b5c84c6ed9b3de9593f0d6ff02df93a0e9ba77
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58159119"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Devuelve al elemento secundario que está en el índice especificado en el nodo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Para `IScriptEntry` objetos que especifican un objeto de función y para `IScriptScriptlet` objetos, este método produce un error porque no hay ningún entradas secundarias.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)