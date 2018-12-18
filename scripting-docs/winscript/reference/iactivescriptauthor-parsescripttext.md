---
title: IActiveScriptAuthor::ParseScriptText | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.ParseScriptText
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::ParseScriptText
ms.assetid: ebe212e8-6789-423d-ad22-92be984dc7ad
caps.latest.revision: 15
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 13e81d96ae817b2117f12cb56fd59759f4c2b849
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645515"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analiza el texto de la secuencia de comandos, se agrega el texto para el motor de creación de script y crea un `IScriptEntry` objeto que se corresponde con el bloque de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT ParseScriptText(  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszCode`  
 [in] Para analizar el texto del script.  
  
 `pszItemName`  
 [in] La dirección de búfer que contiene el nombre del elemento asociado al bloque de script.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final del bloque de script. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador (por ejemplo, dos comillas simples), para detectar el final del bloque de script. Establezca este parámetro en NULL si no hay ningún delimitador para identificar el final del bloque de script.  
  
 `dwCookie`  
 [in] Un valor definido por la aplicación que está asociado a la nueva `IScriptEntry` objeto.  
  
 `dwFlags`  
 [in] No usado.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)