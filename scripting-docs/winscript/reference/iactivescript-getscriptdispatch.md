---
title: 'IActiveScript:: Getscriptdispatch | Documentos de Microsoft'
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScript.GetScriptDispatch
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScript_GetScriptDispatch
ms.assetid: 2092ccd4-1f4c-493a-b5b7-077a70ce95ca
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2a18d6781ca2b7820686b317ad0be5da425ade1f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54097687"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera el `IDispatch` interfaz para los métodos y propiedades asociadas con la secuencia de comandos que se está ejecutando.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrItemName`  
 [in] Dirección de un búfer que contiene el nombre del elemento para que el llamador necesita el objeto de envío asociados. Si este parámetro es `NULL`, contiene el objeto de envío como de sus miembros todas las propiedades y métodos globales definidos por la secuencia de comandos. A través de la `IDispatch` asociado e interfaz `ITypeInfo` interfaz, el host puede llamar a métodos de script o la vista y modificar las variables de secuencia de comandos.  
  
 `ppdisp`  
 [out] Dirección de una variable que recibe un puntero al objeto asociado con los métodos globales y propiedades de la secuencia de comandos. Si el motor de scripting no admite este tipo de objeto, `NULL` se devuelve.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los siguientes valores:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se especificó un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting no se ha cargado o inicializado).|  
|`S_FALSE`|El motor de scripting no admite un objeto de envío; el `ppdisp` parámetro se establece en NULL.|  
  
## <a name="remarks"></a>Comentarios  
 Dado que los métodos y propiedades se pueden agregar mediante una llamada a la [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) interfaz, el `IDispatch` interfaz devuelta por este método puede admitir dinámicamente nuevos métodos y propiedades. De forma similar, el `IDispatch::GetTypeInfo` método debe devolver un nuevo y único `ITypeInfo` cuando se agregan métodos y propiedades de la interfaz. Sin embargo, tenga en cuenta que los motores de lenguaje no deben cambiar la `IDispatch` interfaz en una manera que es incompatible con cualquier anterior `ITypeInfo` interfaz devuelta. Por ejemplo, que implica que nunca se reutilizará el envío (DISPID).  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)