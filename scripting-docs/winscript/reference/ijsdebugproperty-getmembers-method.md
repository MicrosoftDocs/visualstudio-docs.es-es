---
title: "Ijsdebugproperty:: GetMembers (método) | Documentos de Microsoft"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
apiname: IJsDebugProperty.GetMembers
apilocation: jscript9diag.dll
ms.assetid: a32b5372-d9cb-4b9a-9bc2-81b5e1df365c
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 066db431f27eca01fab63d10d0396575b3895527
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="ijsdebugpropertygetmembers-method"></a>IJsDebugProperty::GetMembers (Método)
Obtiene a los miembros de este objeto.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetMembers(  
   JS_PROPERTY_MEMBERS members,  
   IJsEnumDebugProperty **ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `members`  
 [in] Marcas para especificar qué se incluye en la información de miembros.  
  
 `ppEnum`  
 [out] Los miembros del objeto.  
  
## <a name="return-value"></a>Valor devuelto  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jscript9diag.h  
  
## <a name="see-also"></a>Vea también  
 [IJsDebugProperty (Interfaz)](../../winscript/reference/ijsdebugproperty-interface.md)