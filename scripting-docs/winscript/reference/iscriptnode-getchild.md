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
ms.openlocfilehash: 55cd6cf5233e850e4109128e322d3fc5bd0b1355
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086598"
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