---
title: IActiveScriptAuthor::GetLanguageFlags | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 6137f1cd77d2f305a9ff9d51ac49c214e4c4237b
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Devuelve información del idioma.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pgrfasa`  
 [out] Las marcas que contienen información de idioma. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0 x 0001|El idioma prefiere creación de controlador de eventos de secuencia de comandos por el motor en lugar de la aplicación de creación de script.|  
|fasaSupportInternalHandler|0 x 0002|El lenguaje admite controladores de eventos de script creados por el motor de creación de script.|  
|fasaCaseSensitive|0 x 0004|El lenguaje de script distingue mayúsculas de minúsculas.|  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Si el motor de creación de script administra controladores de eventos, la aplicación debe llamar a `CreateChildHandler` desde un `IScriptEntry` objeto. Esto crea una `IScriptScriptlet` objeto que corresponde al controlador de eventos. El motor también agrega un controlador de eventos a la entrada de secuencia de comandos. El controlador de eventos es una función vacía que contiene la información de firma especificado.  
  
 Si la aplicación administra controladores de eventos, debe llamar a `CreateChildHandler` desde un `IScriptNode` objeto que representa un scriptlet de controlador de eventos. Esto crea una `IScriptScriptlet` objeto que está asociado con el scriptlet de controlador de eventos. La aplicación también tiene que agregar una función vacía como un evento de controlador a una nueva o existente `IScriptEntry` objeto.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)