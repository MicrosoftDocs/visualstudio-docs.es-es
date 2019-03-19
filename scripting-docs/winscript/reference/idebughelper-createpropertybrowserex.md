---
title: IDebugHelper::CreatePropertyBrowserEx | Microsoft Docs
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
ms.openlocfilehash: 01e63d1588fd1e25f3415f22450ed5145752d711
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58144581"
---
# <a name="idebughelpercreatepropertybrowserex"></a>IDebugHelper::CreatePropertyBrowserEx
Devuelve un explorador de propiedades que contiene una variante y permite la conversión personalizada de valores VARIANT o tipos VARTYPE en cadenas.  
  
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
 [in] Variante de raíz que examinar.  
  
 `bstrName`  
 [in] Nombre para la raíz.  
  
 `pdat`  
 [in] El subproceso en el que se va a propiedades de la solicitud. Si este parámetro es NULL, no se realiza la ningún cálculo de referencias.  
  
 `pdf`  
 [in] Objeto que proporciona un formato personalizado para las variantes.  
  
 `ppdob`  
 [out] El Explorador de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un explorador de propiedades que contiene una variante y permite la conversión personalizada de valores VARIANT o tipos VARTYPE en cadenas.  
  
## <a name="see-also"></a>Vea también  
 [IDebugHelper::CreatePropertyBrowser](../../winscript/reference/idebughelper-createpropertybrowser.md)   
 [IDebugHelper (interfaz)](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)