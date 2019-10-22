---
title: 'IActiveScript:: Clone | Microsoft Docs'
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
ms.openlocfilehash: fbaad29cb31af26a0f26a1c679a900192fc77041
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575799"
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona el motor de scripting actual (menos cualquier estado de ejecución actual) y devuelve un motor de scripting cargado que no tiene ningún sitio en el subproceso actual. Las propiedades de este nuevo motor de scripting serán idénticas a las propiedades en las que sería el motor de scripting original si se pasase de nuevo al estado inicializado.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppscript`  
 enuncia Dirección de una variable que recibe un puntero a la interfaz [IActiveScript](../../winscript/reference/iactivescript.md) del motor de scripting clonado. El host debe crear un sitio y llamar al método [IActiveScript:: SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) en el nuevo motor de scripting para que esté en el estado inicializado y, por tanto, se pueda usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|No se admite este método.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
  
## <a name="remarks"></a>Comentarios  
 El método `IActiveScript::Clone` es una optimización de `IPersist*::Save`, `CoCreateInstance` y `IPersist*::Load`, por lo que el estado del nuevo motor de scripting debe ser el mismo que si el estado del motor de scripting original se guardara y se cargara en un nuevo motor de scripting. Los elementos con nombre se duplican en el motor de scripting clonado, pero los punteros de objeto específicos de cada elemento se olvidan y se obtienen con el método [IActiveScriptSite:: GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) . Esto permite usar un modelo de objetos idéntico con puntos de entrada por subproceso (un modelo de apartamento).  
  
 Este método se usa para los hosts de servidor multiproceso que pueden ejecutar varias instancias del mismo script. El motor de scripting puede devolver `E_NOTIMPL`, en cuyo caso el host puede lograr el mismo resultado duplicando el estado persistente y creando una nueva instancia del motor de scripting con una interfaz `IPersist*`.  
  
 Se puede llamar a este método desde subprocesos no base sin tener como resultado una llamada no base a objetos host o a la interfaz [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) .  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)