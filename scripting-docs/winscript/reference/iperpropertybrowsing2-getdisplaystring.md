---
title: IPerPropertyBrowsing2::GetDisplayString | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.GetDisplayString
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::GetDisplayString
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e4947ebdeac26ae759fb739dd417607dea885ee5
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54091578"
---
# <a name="iperpropertybrowsing2getdisplaystring"></a>IPerPropertyBrowsing2::GetDisplayString
Obtiene una cadena para mostrar tipos que no son visibles de forma inherente el texto devuelto es un nombre que describe la propiedad y se puede mostrar en interfaz de usuario del llamador.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dispid`  
 [in] Identificador de envío de la propiedad cuyo nombre para mostrar se solicita.  
  
 `pBstr`  
 [out] Puntero a la `BSTR` que contiene el nombre para mostrar para la propiedad identificada por `dispID`.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 La cadena devuelta no es un valor válido de la propiedad. Es simplemente una presentación de la cadena de la propiedad.  
  
## <a name="see-also"></a>Vea también  
 [IPerPropertyBrowsing2 (Interfaz) 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)