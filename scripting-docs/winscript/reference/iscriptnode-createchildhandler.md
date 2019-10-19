---
title: 'Iscriptnode (:: CreateChildHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IScriptNode.CreateChildHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IScriptNode::CreateChildHandler
ms.assetid: 4ce5eb10-1a3f-43b0-a4b7-599a397ed3a2
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e024bb7d6a81b35994edddfe9e71666b0ee8df0
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573596"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Agrega un Scriptlet como una instancia secundaria de un `IScriptNode`.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreateChildHandler(  
   LPCOLESTR          pszDefaultName,  
   LPCOLESTR          *prgpszNames,  
   ULONG              cpszNames,  
   LPCOLESTR          pszEvent,  
   LPCOLESTR          pszDelimiter,  
   ITypeInfo*         ptiSignature,  
   ULONG              iMethodSignature,  
   ULONG              isn,  
   DWORD              dwCookie,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pszDefaultName`  
 de Dirección del nombre predeterminado que se va a asociar al Scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] Una lista de identificadores del nombre completo en el host.  
  
 `cpszNames`  
 de Número de identificadores en el parámetro `prgpszNames`.  
  
 `pszEvent`  
 de La dirección de búfer que identifica el nombre de evento asociado al Scriptlet.  
  
 `pszDelimiter`  
 de Dirección del delimitador de bloque de script final. Para el análisis, el host normalmente usa un delimitador (como dos comillas simples) para detectar el final del bloque de script.  
  
 El delimitador permite el preprocesamiento por parte del motor de creación de scripts. Por ejemplo, el motor podría reemplazar una comilla simple con dos comillas simples para su uso como delimitador. El motor determina cómo se usa el delimitador.  
  
 Se establece en NULL si no se usa ningún delimitador para identificar el final del bloque de script.  
  
 `ptiSignature`  
 de Información de tipo para un objeto de función.  
  
 `iMethodSignature`  
 de Índice de la función en el parámetro `ITypeInfo``ptiSignature`.  
  
 `isn`  
 de Índice del elemento secundario del elemento primario.  
  
 `dwCookie`  
 de Un valor definido por la aplicación que se utiliza para asociar la entrada con el objeto host.  
  
 `ppse`  
 enuncia Dirección de una variable que recibe un puntero a la interfaz `IScriptEntry` de la instancia secundaria.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Un Scriptlet especifica un controlador de eventos. Este método crea un Scriptlet si lo llama un objeto `IScriptNode` que representa una página web. Este método no se realiza correctamente si lo llaman otras interfaces.  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iscriptnode (](../../winscript/reference/iscriptnode-interface.md)  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)