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
ms.openlocfilehash: 2e7f6cc265815db4acd847270b28c3e744257fa0
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086689"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Devuelve el scriptlet que tiene los atributos especificados.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
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
 [in] El `IDispatch` objeto que corresponde a la `NamedItem` al que está asociado el scriptlet.  
  
 `pszItem`  
 [in] La dirección de búfer del identificador del nombre completo del scriptlet en el host de nivel superior.  
  
 `pszSubItem`  
 [in] La dirección de búfer del identificador del nombre completo del scriptlet en el host de segundo nivel. Se establece en NULL si el nombre tiene un solo nivel.  
  
 `pszEvent`  
 [in] La dirección de un búfer que contiene el nombre del evento. El scriptlet es un controlador de eventos para este evento.  
  
 `ppse`  
 [out] La dirección de una variable que recibe un puntero a la `IScriptEntry` interfaz del scriptlet que tiene los atributos especificados.  
  
## <a name="return-value"></a>Valor devuelto  
 Una clase `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [IActiveScriptAuthor (interfaz)](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)