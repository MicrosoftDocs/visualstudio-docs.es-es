---
title: Método Ijsenumdebugproperty | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsEnumDebugProperty.Next
apilocation:
- jscript9diag.dll
ms.assetid: 9fad1893-483a-440c-88c1-469494212300
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 9e6b0e3499f9420d42660880f616d2d0873d7a0f
ms.sourcegitcommit: 116e9614867e0b3c627ce9001012a4c39435a42b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/08/2019
ms.locfileid: "54086780"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next (Método)
Lee las propiedades para este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `count`  
 [in] El número de propiedades que se va a leer.  
  
 `ppDebugProperty`  
 [out] Objeto que representa el Explorador de propiedades.  
  
 `pActualCount`  
 [out] El número real de las propiedades del objeto.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsEnumDebugProperty (Interfaz)](../../winscript/reference/ijsenumdebugproperty-interface.md)