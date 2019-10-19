---
title: 'IJsEnumDebugProperty:: Next (método) | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
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
ms.openlocfilehash: 48c4506d783093395b2d88b7a71d56e3a89d24e8
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2019
ms.locfileid: "72573984"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next (Método)
Lee las propiedades de este objeto.  
  
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
 de Número de propiedades que se van a leer.  
  
 `ppDebugProperty`  
 enuncia Objeto que representa el explorador de propiedades.  
  
 `pActualCount`  
 enuncia Número real de propiedades del objeto.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag. h  
  
## <a name="see-also"></a>Vea también  
 [IJsEnumDebugProperty (Interfaz)](../../winscript/reference/ijsenumdebugproperty-interface.md)