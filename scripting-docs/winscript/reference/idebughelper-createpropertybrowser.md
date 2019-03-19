---
title: IDebugHelper::CreatePropertyBrowser | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugHelper.CreatePropertyBrowser
apilocation:
- pdm.dll
helpviewer_keywords:
- IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 4fc1e4365deea4a3981d9cf457a2c0af37edcd43
ms.sourcegitcommit: d3a485d47c6ba01b0fc9878cbbb7fe88755b29af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/19/2019
ms.locfileid: "58158911"
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Devuelve un explorador de propiedades que encapsula una variante.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
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
  
 `ppdob`  
 [out] El Explorador de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un explorador de propiedades que encapsula una variante.  
  
## <a name="see-also"></a>Vea también  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper (interfaz)](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)