---
title: IActiveScriptSite::GetDocVersionString | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: b4b009c9eb40b2935a5b1aeca0d551819462bafc
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24724545"
---
# <a name="iactivescriptsitegetdocversionstring"></a>IActiveScriptSite::GetDocVersionString
Recupera una cadena definida por el host que identifica de forma única la versión del documento actual. Si ha cambiado el documento relacionado fuera del ámbito de la secuencia de comandos de Windows (como en el caso de una página HTML que se está editando con el Bloc de notas), el motor de scripting puede guardar junto con su estado persistente, forzar una nueva compilación la próxima vez que se carga el script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetDocVersionString(  
    BSTR *pbstrVersionString  // address of document version string  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pstrVersionString`  
 [out] Dirección de la cadena de versión de documento definida por el host.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve `S_OK` si se realiza correctamente, o `E_NOTIMPL` si no se admite este método.  
  
## <a name="remarks"></a>Comentarios  
 Si `E_NOTIMPL` se devuelve, el motor de scripting debe asumir que la secuencia de comandos está sincronizada con el documento.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md)