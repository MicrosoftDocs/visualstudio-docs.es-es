---
title: IActiveScriptSite::GetDocVersionString | Microsoft Docs
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
ms.openlocfilehash: 7327b71329c1f476eab9c27d5e0d5a047664abfa
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58147961"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera una cadena definida por el host que identifica la versión actual del documento. Si el documento relacionado ha cambiado fuera del ámbito de la secuencia de comandos de Windows (como en el caso de una página HTML que se está editando con el Bloc de notas), el motor de scripting puede guardar junto con su estado persistente, forzar una nueva compilación la próxima vez que se carga el script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrVersionString`  
 [out] Dirección de la cadena de versión de documento definido por el host.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_NOTIMPL` si no se admite este método.  
  
## <a name="remarks"></a>Comentarios  
 Si `E_NOTIMPL` se devuelve, el motor de scripting debe suponer que la secuencia de comandos está sincronizada con el documento.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)