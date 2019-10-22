---
title: 'IActiveScript:: GetScriptDispatch | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: ba53f2eccde18bd5b2d9c609ea680b50cb7261c9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72575762"
---
# <a name="iactivescriptgetscriptdispatch"></a>IActiveScript::GetScriptDispatch
Recupera la interfaz de `IDispatch` para los métodos y propiedades asociados con el script que se está ejecutando actualmente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetScriptDispatch(  
    LPCOLESTR pstrItemName  // address of item name  
    IDispatch **ppdisp      // receives IDispatch pointer  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrItemName`  
 de Dirección de un búfer que contiene el nombre del elemento para el que el autor de la llamada necesita el objeto de envío asociado. Si este parámetro es `NULL`, el objeto Dispatch contiene como miembros todos los métodos y propiedades globales definidos por el script. A través de la interfaz de `IDispatch` y la interfaz de `ITypeInfo` asociada, el host puede invocar métodos de script o ver y modificar variables de script.  
  
 `ppdisp`  
 enuncia Dirección de una variable que recibe un puntero al objeto asociado a los métodos y propiedades globales del script. Si el motor de scripting no admite este tipo de objeto, se devuelve `NULL`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve uno de los valores siguientes:  
  
|Valor devuelto|Significado|  
|------------------|-------------|  
|`S_OK`|Correcto.|  
|`E_INVALIDARG`|Un argumento no era válido.|  
|`E_POINTER`|Se ha especificado un puntero no válido.|  
|`E_UNEXPECTED`|No se esperaba la llamada (por ejemplo, el motor de scripting aún no se ha cargado o inicializado).|  
|`S_FALSE`|El motor de scripting no admite un objeto Dispatch; el parámetro `ppdisp` está establecido en NULL.|  
  
## <a name="remarks"></a>Comentarios  
 Dado que los métodos y las propiedades se pueden agregar llamando a la interfaz [IActiveScriptParse](../../winscript/reference/iactivescriptparse.md) , la interfaz `IDispatch` devuelta por este método puede admitir dinámicamente nuevos métodos y propiedades. Del mismo modo, el método `IDispatch::GetTypeInfo` debe devolver una nueva interfaz de `ITypeInfo` única cuando se agregan métodos y propiedades. Tenga en cuenta, sin embargo, que los motores de lenguaje no deben cambiar la interfaz `IDispatch` de una manera que sea incompatible con cualquier interfaz de `ITypeInfo` anterior devuelta. Esto implica, por ejemplo, que los DISPID nunca se volverán a usar.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScript](../../winscript/reference/iactivescript.md)