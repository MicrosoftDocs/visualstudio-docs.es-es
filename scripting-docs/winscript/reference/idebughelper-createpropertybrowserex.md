---
title: 'Idebughelper (:: CreatePropertyBrowserEx | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowserEx
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowserEx
ms.assetid: 87ad322f-09da-4ce8-bb68-0b0bbeec645b
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4d64d9dad54e029dc4c76e8b7e6c7a3f0299b0cb
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576501"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Devuelve un explorador de propiedades que ajusta una variante y permite la conversión personalizada de valores VARIANT o tipos VARTYPE en cadenas.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreatePropertyBrowserEx(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugFormatter*          pdf,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvar`  
 de Variante raíz que se va a examinar.  
  
 `bstrName`  
 de Nombre que se va a asignar a la raíz.  
  
 `pdat`  
 de Subproceso en el que se van a solicitar propiedades. Si este parámetro es NULL, no se realiza ninguna serialización.  
  
 `pdf`  
 de Objeto que proporciona el formato personalizado para las variantes.  
  
 `ppdob`  
 enuncia Explorador de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un explorador de propiedades que ajusta una variante y permite la conversión personalizada de valores VARIANT o tipos VARTYPE en cadenas.  
  
## <a name="see-also"></a>Vea también  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
   de la [interfaz idebughelper (](../../winscript/reference/idebughelper-interface.md)  
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)