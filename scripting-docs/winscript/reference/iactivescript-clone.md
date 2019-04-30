---
title: IActiveScript::Clone | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.Clone
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: bec912596c792a67f65434062bc0d0ed11bd3fb9
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62935710"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona el motor de scripting actual (menos cualquier estado de ejecución actual), devolviendo un motor de scripting cargado que no tenga ningún sitio en el subproceso actual. Las propiedades de este nuevo motor de scripting será idénticas a las propiedades que el motor de scripting original estaría en si se han pasado al estado inicializado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppscript`  
 [out] Dirección de una variable que recibe un puntero a la [IActiveScript](../../winscript/reference/iactivescript.md) interfaz del motor de scripting clonado. El host debe crear un sitio y llamar a la [IActiveScript:: Setscriptsite](../../winscript/reference/iactivescript-setscriptsite.md) método en el nuevo motor de scripting para que esté en estado inicializado y, por lo tanto, puede usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|No se admite este método.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting no se ha cargado o inicializado).|  
  
## <a name="remarks"></a>Comentarios  
 El `IActiveScript::Clone` método es una optimización de `IPersist*::Save`, `CoCreateInstance`, y `IPersist*::Load`, por lo que el estado del motor de scripting nuevo debe ser el mismo que si se guarda el estado del motor de scripting original y se cargan en un nuevo motor de scripting. Elementos con nombre se duplican en el motor de scripting clonado, pero se olvidan de punteros a objetos específicos para cada elemento y se obtienen con el [GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) método. Esto permite un modelo de objetos idéntico con puntos de entrada por subproceso (un modelo de apartamento) que se usará.  
  
 Este método se usa para los hosts de servidor multiproceso que se pueden ejecutar varias instancias de la misma secuencia de comandos. El motor de scripting puede devolver `E_NOTIMPL`, en cuyo caso el host puede lograr el mismo resultado duplicando el estado persistente y crear una nueva instancia del motor de scripting con un `IPersist*` interfaz.  
  
 Este método se pueda llamar desde subprocesos no son de base sin resultante en una llamada que no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)