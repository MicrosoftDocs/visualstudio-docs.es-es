---
title: 'Iscriptnode (:: GetChild | Microsoft Docs'
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
ms.openlocfilehash: 27ddde527be1ea4148e4166581ab2cb1a71d15f7
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573563"
---
# <a name="iscriptnodegetchild"></a>IScriptNode::GetChild
Devuelve el elemento secundario que se encuentra en el índice especificado del nodo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetChild(  
   ULONG              isn,  
   IScriptNode        **ppsn  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `isn`  
 de Índice del elemento secundario del elemento primario.  
  
 `ppsn`  
 enuncia Dirección de una variable que recibe un puntero a la interfaz `IScriptNode` de la instancia secundaria.  
  
 En el caso de `IScriptNode` objetos que representan una página web, este parámetro devuelve un objeto que contiene un bloque de script.  
  
 En el caso de `IScriptEntry` objetos que especifican un bloque de script, este parámetro devuelve un objeto que especifica una función.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 En el caso de `IScriptEntry` objetos que especifican un objeto de función y para objetos `IScriptScriptlet`, este método produce un error porque no hay entradas secundarias.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (Interfaz)](../../winscript/reference/iscriptnode-interface.md)