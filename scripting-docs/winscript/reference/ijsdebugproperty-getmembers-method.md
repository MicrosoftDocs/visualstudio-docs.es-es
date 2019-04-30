---
title: Método Ijsdebugproperty | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IJsDebugProperty.GetMembers
apilocation:
- jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: 4
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 3be31a0f02869ea740809fb68dbddf48843b2f3e
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62793674"
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers (Método)
Obtiene a los miembros de este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `members`  
 [in] Marcadores que especifican qué se incluye en la información del miembro.  
  
 `ppEnum`  
 [out] Los miembros del objeto.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugProperty (Interfaz)](../../winscript/reference/ijsdebugproperty-interface.md)