---
title: 'Iscriptnode (:: CreateChildEntry | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode. CreateChildEntry
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildEntry
ms.assetid: b9682505-4457-40e9-8691-235843637506
caps.latest.revision: 17
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c58ff83c43a1418e6fb7bd8945afa181af60c68a
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573617"
---
# <a name="iscriptnode-createchildentry"></a>IScriptNode:: CreateChildEntry
Agrega una instancia secundaria de `IScriptEntry`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateChildEntry(  
   ULONG              isn,  
   DWORD              dwCookie,  
   LPCOLESTR          pszDelimiter,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `isn`  
 de Índice del elemento secundario del elemento primario.  
  
 `dwCookie`  
 de Un valor definido por la aplicación que se usa para asociar la entrada secundaria con el objeto host.  
  
 `pszDelimiter`  
 de Dirección del delimitador de bloque de script final. Para el análisis, el host normalmente usa un delimitador (como dos comillas simples) para detectar el final del bloque de script.  
  
 El delimitador permite que el motor de creación de scripts proporcione preprocesamiento. Por ejemplo, el motor podría reemplazar una comilla simple con dos comillas simples para su uso como delimitador. El motor determina cómo se usa el delimitador.  
  
 Se establece en NULL si un delimitador no marca el final del bloque de script.  
  
 `ppse`  
 enuncia Dirección de una variable que recibe un puntero a la interfaz `IScriptEntry` de la instancia secundaria.  
  
 En el caso de `IScriptNode` objetos que representan una página web, este parámetro devuelve una instancia de `IScriptEntry` que especifica un bloque de script.  
  
 En el caso de `IScriptEntry` objetos que representan un bloque de script, este parámetro devuelve una instancia de `IScriptEntry` que especifica un objeto de función.  
  
 En el caso de `IScriptEntry` objetos que representan un objeto de función, este método produce un error.  
  
 En el caso de los objetos `IScriptScriptlet`, este método produce un error.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 La interfaz de `IScriptNode` representa una página web o sus elementos. La interfaz `IScriptEntry` (que se deriva de `IScriptNode`) representa un bloque de script o un objeto de función. La interfaz `IScriptScriptlet` (que se deriva de `IScriptEntry`) representa un controlador de eventos.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iscriptnode (](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)