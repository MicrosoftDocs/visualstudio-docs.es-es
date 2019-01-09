---
title: IScriptNode::CreateChildHandler | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
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
ms.openlocfilehash: 2ef4c9318cb13459ab787878218bf7ca68052f29
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54094190"
---
# <a name="iscriptnodecreatechildhandler"></a>IScriptNode::CreateChildHandler
Agrega un scriptlet como una instancia secundaria de un `IScriptNode`.  
  
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
 [in] La dirección del nombre predeterminado para asociar el scriptlet.  
  
 `prgpszNames`  
 [in, size_is (`cpszNames`)] lista de identificadores de nombre completo del host.  
  
 `cpszNames`  
 [in] El número de identificadores en el `prgpszNames` parámetro.  
  
 `pszEvent`  
 [in] La dirección de búfer que identifica el nombre de evento asociado al scriptlet.  
  
 `pszDelimiter`  
 [in] La dirección del delimitador final del bloque de script. Para el análisis, el host normalmente utiliza un delimitador (por ejemplo, dos comillas simples), para detectar el final del bloque de script.  
  
 El delimitador permite por el motor de creación de script de preprocesamiento. Por ejemplo, el motor podría reemplazar una comilla simple con dos comillas simples para su uso como un delimitador. El motor determina cómo se usa el delimitador.  
  
 Se establece en NULL si no hay delimitador se utiliza para identificar el final del bloque de script.  
  
 `ptiSignature`  
 [in] La información de tipo para un objeto de función.  
  
 `iMethodSignature`  
 [in] El índice de la función en el `ITypeInfo``ptiSignature` parámetro.  
  
 `isn`  
 [in] El índice del elemento secundario en el elemento primario.  
  
 `dwCookie`  
 [in] Un valor definido por la aplicación que se usa para asociar la entrada con el objeto host.  
  
 `ppse`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptEntry` interfaz de la instancia secundaria.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Scriptlet especifica un controlador de eventos. Este método crea un scriptlet si se llama un `IScriptNode` objeto que representa una página Web. Este método no se realiza correctamente si se llama mediante otras interfaces.  
  
## <a name="see-also"></a>Vea también  
 [IScriptNode (interfaz)](../../winscript/reference/iscriptnode-interface.md)   
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)