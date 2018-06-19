---
title: IActiveScriptAuthor::GetEventHandler | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IActiveScriptAuthor.GetEventHandler
apilocation:
- scrobj.dll
helpviewer_keywords:
- IActiveScriptAuthor::GetEventHandler
ms.assetid: 87c7a71d-46b9-448c-b34d-394105e20982
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 2b09f900162b6dba82696c946b53ab131691530c
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24645585"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Devuelve el scriptlet que tiene los atributos especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetEventHandler(  
   IDispatch          *pdisp,  
   LPCOLESTR          pszItem,  
   LPCOLESTR          pszSubItem,  
   LPCOLESTR          pszEvent,  
   IScriptEntry       **ppse  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pdisp`  
 [in] El `IDispatch` objeto que corresponde a la `NamedItem` a la que está asociado el scriptlet.  
  
 `pszItem`  
 [in] La dirección del búfer del identificador del nivel superior del nombre completo scriptlet en el host.  
  
 `pszSubItem`  
 [in] La dirección del búfer del identificador de segundo nivel del nombre completo scriptlet en el host. Se establece en NULL si el nombre tiene un solo nivel.  
  
 `pszEvent`  
 [in] La dirección de un búfer que contiene el nombre del evento. El scriptlet es un controlador de eventos para este evento.  
  
 `ppse`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptEntry` interfaz del scriptlet que tiene los atributos especificados.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)