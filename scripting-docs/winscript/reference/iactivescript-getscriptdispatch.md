---
title: IActiveScript::GetScriptDispatch | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IActiveScript.GetScriptDispatch
apilocation: scrobj.dll
helpviewer_keywords: IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5b2f09934cf6d2bb28f7dae93d0bf49c8dc7437d
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera el `IDispatch` interfaz para los métodos y propiedades asociados a la secuencia de comandos que se está ejecutando.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrItemName`  
 [in] Dirección de un búfer que contiene el nombre del elemento para el que el llamador necesita el objeto de envío asociados. Si este parámetro es `NULL`, contiene el objeto de envío como miembros todos los métodos globales y las propiedades definidas por la secuencia de comandos. A través de la `IDispatch` asociado e interfaz `ITypeInfo` interfaz, el host puede llamar a métodos de secuencia de comandos o la vista y modificar variables de secuencia de comandos.  
  
 `ppdisp`  
 [out] Dirección de una variable que recibe un puntero al objeto asociado con los métodos globales y propiedades de la secuencia de comandos. Si el motor de scripting no admite este tipo de objeto, `NULL` se devuelve.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting se aún no ha cargado o inicializar).|  
|`S_FALSE`|El motor de scripting no es compatible con un objeto de envío; el `ppdisp` parámetro se establece en NULL.|  
  
## <a name="remarks"></a>Comentarios  
 Porque se pueden agregar métodos y propiedades mediante una llamada a la [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interfaz, el `IDispatch` interfaz devuelta por este método puede admitir dinámicamente nuevos métodos y propiedades. De forma similar, el `IDispatch::GetTypeInfo` método debe devolver un nuevo y único `ITypeInfo` cuando se agregan métodos y propiedades de la interfaz. Sin embargo, tenga en cuenta que los motores de idioma no deben cambiar la `IDispatch` interfaz en un modo que sean incompatibles con cualquier anterior `ITypeInfo` interfaz devuelta. Por ejemplo, que implica que los identificadores DispId nunca se reutilizará.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)