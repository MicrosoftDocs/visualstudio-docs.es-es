---
title: IPerPropertyBrowsing2::SetPredefinedValue | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IPerPropertyBrowsing2.SetPredefinedValue
apilocation:
- scrobj.dll
helpviewer_keywords:
- IPerPropertyBrowsing2::SetPredefinedValue
ms.assetid: 3aff5300-c5a4-4d9b-9d47-a75b64014ac4
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: ac3b2e6cf61bdd6b9587cd390494d4074ce6361d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49828993"
---
# <a name="iperpropertybrowsing2setpredefinedvalue"></a>IPerPropertyBrowsing2::SetPredefinedValue
Establece el valor de la propiedad especificada por `dispID`. El valor predefinido es identificado por el token `dwCookie.`  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT SetPredefinedValue(  
   DISPID  dispid,  
   DWORD  dwCookie  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dispid`  
 [in] Identificador de envío de la propiedad para el que se establece un valor predefinido.  
  
 `dwCookie`  
 [in] Símbolo (token) que identifica el valor que se va a establecer.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IPerPropertyBrowsing2 (Interfaz) 1](../../winscript/reference/iperpropertybrowsing2-interface-1.md)