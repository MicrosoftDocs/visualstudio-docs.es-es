---
title: 'Iactivescriptauthor (:: GetLanguageFlags | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetLanguageFlags
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetLanguageFlags
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 68da16513050bd87642be2c96212a330a0916608
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576201"
---
# <a name="iactivescriptauthorgetlanguageflags"></a>IActiveScriptAuthor::GetLanguageFlags
Devuelve información de idioma.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pgrfasa`  
 enuncia Marcas que contienen información de idioma. Puede ser una combinación de los siguientes valores:  
  
|Constante|Valor|Descripción|  
|--------------|-----------|-----------------|  
|fasaPreferInternalHandler|0x0001|El lenguaje prefiere que el motor de creación de scripts cree el controlador de eventos de script en lugar de la aplicación.|  
|fasaSupportInternalHandler|0x0002|El lenguaje admite controladores de eventos de script creados por el motor de creación de scripts.|  
|fasaCaseSensitive|0x0004|El lenguaje de script distingue mayúsculas de minúsculas.|  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Si el motor de creación de scripts administra controladores de eventos, la aplicación debe llamar a `CreateChildHandler` desde un objeto `IScriptEntry`. Esto crea un objeto `IScriptScriptlet` que corresponde al controlador de eventos. El motor también agrega un controlador de eventos a la entrada de script. El controlador de eventos es una función vacía que contiene la información de firma especificada.  
  
 Si la aplicación administra controladores de eventos, debe llamar a `CreateChildHandler` desde un objeto `IScriptNode` que representa un Scriptlet del controlador de eventos. Esto crea un objeto de `IScriptScriptlet` que está asociado al controlador de eventos Scriptlet. La aplicación también tiene que agregar una función vacía como controlador de eventos a un objeto `IScriptEntry` nuevo o existente.  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (Interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)