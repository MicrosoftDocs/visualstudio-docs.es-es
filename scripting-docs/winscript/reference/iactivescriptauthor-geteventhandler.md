---
title: 'Iactivescriptauthor (:: GetEventHandler | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: c69b32f0040ea6d52e0712b8e1813cc5a0b40c58
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576226"
---
# <a name="iactivescriptauthorgeteventhandler"></a>IActiveScriptAuthor::GetEventHandler
Devuelve el Scriptlet que tiene los atributos especificados.  
  
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
 de Objeto `IDispatch` que corresponde al `NamedItem` al que se adjunta el Scriptlet.  
  
 `pszItem`  
 de La dirección de búfer del identificador de nivel superior del nombre completo de Scriptlet en el host.  
  
 `pszSubItem`  
 de Dirección de búfer del identificador de segundo nivel del nombre completo de Scriptlet en el host. Se establece en NULL si el nombre tiene un solo nivel.  
  
 `pszEvent`  
 de Dirección de un búfer que contiene el nombre del evento. Scriptlet es un controlador de eventos para este evento.  
  
 `ppse`  
 enuncia Dirección de una variable que recibe un puntero a la interfaz `IScriptEntry` del Scriptlet que tiene los atributos especificados.  
  
## <a name="return-value"></a>Valor devuelto  
 Interfaz `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 @No__t_1 de la [interfaz iactivescriptauthor (](../../winscript/reference/iactivescriptauthor-interface.md)  
 [IScriptEntry (Interfaz)](../../winscript/reference/iscriptentry-interface.md)