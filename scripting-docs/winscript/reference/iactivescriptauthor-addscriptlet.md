---
title: IActiveScriptAuthor::AddScriptlet | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 10
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 62499afe87a3d7dae31e609c9ce88f41e9d993a9
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54089217"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
El scriptlet de código se agrega como elemento secundario del nivel raíz `IScriptNode` objeto. En el host, el nombre completo del scriptlet puede tener sólo dos niveles.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT AddScriptlet(  
   LPCOLESTR pszDefaultName,  
   LPCOLESTR pszCode,  
   LPCOLESTR pszItemName,  
   LPCOLESTR pszSubItemName,  
   LPCOLESTR pszEventName,  
   LPCOLESTR pszDelimiter,  
   DWORD dwCookie,  
   DWORD dwFlags  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszDefaultName`  
 [in] La dirección del nombre predeterminado para asociar el scriptlet.  
  
 `pszCode`  
 [in] La dirección del texto del scriptlet.  
  
 `pszItemName`  
 [in] La dirección de búfer del identificador del nombre completo del scriptlet en el host de nivel superior.  
  
 `pszSubItemName`  
 [in] La dirección de búfer del identificador del nombre completo del scriptlet en el host de segundo nivel. Se establece en NULL si el nombre tiene un solo nivel.  
  
 `pszEventName`  
 [in] La dirección de un búfer que contiene el nombre del evento para el que el scriptlet es un controlador de eventos.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final del bloque de script. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente utiliza un delimitador (por ejemplo, dos comillas simples), para detectar el final del bloque de script. Si un delimitador no marca el final del bloque de script, establezca este parámetro en NULL.  
  
 `dwCookie`  
 [in] Un valor definido por la aplicación que se utiliza para asociar un objeto host en el scriptlet.  
  
 `dwFlags`  
 [in] No se utiliza.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)