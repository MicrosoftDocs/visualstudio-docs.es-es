---
title: IActiveScript::Clone | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_Clone
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4b0b83bcf86bcc56701d11f22640df966334697b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptclone"></a>IActiveScript::Clone
Clona el motor de scripting actual (menos cualquier estado de ejecución actual), devolver un motor de scripting cargado con ningún sitio en el subproceso actual. Las propiedades de este nuevo motor de scripting sean idénticas a las propiedades que debería tener el motor de scripting original si se han pasado al estado inicializado.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `ppscript`  
 [out] Dirección de una variable que recibe un puntero a la [IActiveScript](../../winscript/reference/iactivescript.md) interfaz del motor de scripting clonado. El host debe crear un sitio y llaman a la [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) método en el nuevo motor de scripting para que esté en el estado de inicialización y, por lo tanto, puede usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_NOTIMPL`|No se admite este método.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
  
## <a name="remarks"></a>Comentarios  
 El `IActiveScript::Clone` método es una optimización de `IPersist*::Save`, `CoCreateInstance`, y `IPersist*::Load`, por lo que el estado del nuevo motor de secuencias de comandos debe ser el mismo que si el estado del motor de scripting original se guarda y se cargan en un nuevo motor de scripting. Elementos con nombre se duplican en el motor de scripting clonado, pero se olvida efectuar de punteros a objetos específicos para cada elemento y se obtienen con el [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md) método. Esto permite que un modelo de objetos idénticos con puntos de entrada por subproceso (un modelo de apartamento) que se usará.  
  
 Este método se usa para los hosts de servidor multiproceso que se pueden ejecutar varias instancias de la misma secuencia de comandos. El motor de scripting puede devolver `E_NOTIMPL`, en cuyo caso el host puede lograr el mismo resultado duplicando el estado persistente y crear una nueva instancia del motor de secuencias de comandos con un `IPersist*` interfaz.  
  
 Este método se pueda llamar desde subprocesos no sea de base sin resultante en una llamada no sea de base a los objetos de host o a la [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md) interfaz.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)