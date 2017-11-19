---
title: IDebugHelper::CreatePropertyBrowser | Documentos de Microsoft
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IDebugHelper.CreatePropertyBrowser
apilocation: pdm.dll
helpviewer_keywords: IDebugHelper::CreatePropertyBrowser
ms.assetid: 2fa819cf-c7f7-4bd7-b018-ea33b804ba8f
caps.latest.revision: "8"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f728068b6d1db6fe70a084ae680f32a78a0a2760
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="idebughelpercreatepropertybrowser"></a>IDebugHelper::CreatePropertyBrowser
Devuelve un explorador de propiedades que contiene una variante.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT CreatePropertyBrowser(  
   VARIANT*                  pvar,  
   LPCOLESTR                 bstrName,  
   IDebugApplicationThread*  pdat,  
   IDebugProperty**          ppdob  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `pvar`  
 [in] Variante de raíz para examinar.  
  
 `bstrName`  
 [in] Nombre que se asigna a la raíz.  
  
 `pdat`  
 [in] El subproceso en el que se puede solicitar propiedades. Si este parámetro es NULL, no se realiza ningún cálculo de referencias.  
  
 `ppdob`  
 [out] El Explorador de propiedades.  
  
## <a name="return-value"></a>Valor devuelto  
 El método devuelve un objeto `HRESULT`. Entre los valores posibles se incluyen los que se indican en la tabla siguiente, entre otros.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|`S_OK`|El método se realizó correctamente.|  
  
## <a name="remarks"></a>Comentarios  
 Este método devuelve un explorador de propiedades que contiene una variante.  
  
## <a name="see-also"></a>Vea también  
 [IDebugHelper::CreatePropertyBrowserEx](../../winscript/reference/idebughelper-createpropertybrowserex.md)   
 [IDebugHelper (interfaz)](../../winscript/reference/idebughelper-interface.md)   
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)