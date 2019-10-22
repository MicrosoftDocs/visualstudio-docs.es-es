---
title: 'IActiveScriptSite:: GetDocVersionString | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptSite.GetDocVersionString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptSite_GetDocVersionString
ms.assetid: ab3f892d-06d3-4cb5-9ea5-20c4a1e518cd
caps.latest.revision: 7
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8ecc592b6b7fcae5f516a3c1dd111c027e67b6dc
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72571129"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera una cadena definida por el host que identifica de forma única la versión del documento actual. Si el documento relacionado ha cambiado fuera del ámbito de la secuencia de comandos de Windows (como en el caso de una página HTML que se está editando con el Bloc de notas), el motor de scripting puede guardar esto junto con su estado persistente y forzar una recompilación la próxima vez que se cargue el script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrVersionString`  
 enuncia Dirección de la cadena de versión del documento definido por el host.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_NOTIMPL` si no se admite este método.  
  
## <a name="remarks"></a>Comentarios  
 Si se devuelve `E_NOTIMPL`, el motor de scripting debe suponer que el script está sincronizado con el documento.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)