---
title: 'Iactivescriptauthor (:: AddScriptlet | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 3a349a848f282e6b3a228c7b17009e0261801be5
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72577985"
---
# <a name="iactivescriptauthoraddscriptlet"></a>IActiveScriptAuthor::AddScriptlet
Agrega un Scriptlet de código como elemento secundario del nivel de raíz `IScriptNode` objeto. En el host, el nombre completo del Scriptlet solo puede tener dos niveles.  
  
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
 de Dirección del nombre predeterminado que se va a asociar al Scriptlet.  
  
 `pszCode`  
 de Dirección del texto del Scriptlet.  
  
 `pszItemName`  
 de La dirección de búfer del identificador de nivel superior del nombre completo de Scriptlet en el host.  
  
 `pszSubItemName`  
 de Dirección de búfer del identificador de segundo nivel del nombre completo de Scriptlet en el host. Se establece en NULL si el nombre tiene un solo nivel.  
  
 `pszEventName`  
 de Dirección de un búfer que contiene el nombre del evento para el que el Scriptlet es un controlador de eventos.  
  
 `pszDelimiter`  
 de Dirección del delimitador de bloque de script final. Cuando `pszCode` se analiza desde un flujo de texto, el host normalmente usa un delimitador (como dos comillas simples) para detectar el final del bloque de script. Establezca este parámetro en NULL si un delimitador no marca el final del bloque de script.  
  
 `dwCookie`  
 de Un valor definido por la aplicación que se usa para asociar el Scriptlet a un objeto host.  
  
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