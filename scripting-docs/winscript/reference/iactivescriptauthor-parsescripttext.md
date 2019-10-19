---
title: Iactivescriptauthor (::P arseScriptText | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 90d5ab0fa700ed29b5fb37b1c48617cedec871b9
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576152"
---
# <a name="iactivescriptauthorparsescripttext"></a>IActiveScriptAuthor::ParseScriptText
Analiza el texto del script, agrega el texto al motor de creación de scripts y crea un objeto `IScriptEntry` que corresponde al bloque de script.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 de Texto del script que se va a analizar.  
  
 `pszItemName`  
 de La dirección del búfer que contiene el nombre del elemento asociado al bloque de script.  
  
 `pszDelimiter`  
 de Dirección del delimitador de bloque de script final. Cuando `pszCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador (como dos comillas simples) para detectar el final del bloque de script. Establezca este parámetro en NULL si no hay ningún delimitador para identificar el final del bloque de script.  
  
 `dwCookie`  
 de Un valor definido por la aplicación que está asociado al nuevo objeto `IScriptEntry`.  
  
 `dwFlags`  
 de No se usa.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)