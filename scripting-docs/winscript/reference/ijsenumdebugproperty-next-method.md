---
title: 'Ijsenumdebugproperty:: Next (método) | Documentos de Microsoft'
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
ms.openlocfilehash: b8c85601709bb727549152ffdb01e15dbd84e510
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
ms.locfileid: "24728825"
---
# <a name="ijsenumdebugpropertynext-method"></a>IJsEnumDebugProperty::Next (Método)
Lee las propiedades para este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT Next(  
   ULONG count,  
   IJsDebugProperty **ppDebugProperty,  
   ULONG *pActualCount  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `count`  
 [in] El número de propiedades para leer.  
  
 `ppDebugProperty`  
 [out] Objeto que representa el Explorador de propiedades.  
  
 `pActualCount`  
 [out] El número real de propiedades del objeto.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsEnumDebugProperty (Interfaz)](../../winscript/reference/ijsenumdebugproperty-interface.md)