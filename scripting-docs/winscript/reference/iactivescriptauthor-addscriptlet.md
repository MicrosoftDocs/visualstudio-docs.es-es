---
title: IActiveScriptAuthor::AddScriptlet | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.AddScriptlet
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::AddScriptlet
ms.assetid: 879a6651-f187-4934-b130-c1247549900b
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b21f906a73a313bf775683ba63738adb25af0007
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Agrega un Subscript de código como un elemento secundario del nivel raíz `IScriptNode` objeto. En el host, el nombre completo de la scriptlet puede tener sólo dos niveles.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
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
 [in] La dirección del texto scriptlet.  
  
 `pszItemName`  
 [in] La dirección del búfer del identificador del nivel superior del nombre completo scriptlet en el host.  
  
 `pszSubItemName`  
 [in] La dirección del búfer del identificador de segundo nivel del nombre completo scriptlet en el host. Se establece en NULL si el nombre tiene un solo nivel.  
  
 `pszEventName`  
 [in] La dirección de un búfer que contiene el nombre del evento para el que el scriptlet es un controlador de eventos.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final del bloque de script. Cuando `pszCode` se analiza desde una secuencia de texto, el host normalmente usa un delimitador (por ejemplo, dos comillas simples), para detectar el final del bloque de script. Establezca este parámetro en NULL si un delimitador no marcar el final del bloque de script.  
  
 `dwCookie`  
 [in] Un valor definido por la aplicación que se utiliza para asociar el scriptlet con un objeto de host.  
  
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