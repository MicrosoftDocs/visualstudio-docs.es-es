---
title: IDebugProperty::EnumMembers | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.EnumMembers
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::EnumMembers
ms.assetid: 8ce398a5-6452-4804-ae8f-5c54cd11c661
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 07ad47ee8d0232df5f528db659def421475e7b33
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49924250"
---
# <a name="idebugpropertyenummembers"></a>IDebugProperty::EnumMembers
Enumera a los miembros de una propiedad.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT EnumMembers (  
   DBGPROP_INFO_FLAGSdwFieldSpec,  
   UINTnRadix,  
   REFIIDrefiid,  
   IEnumDebugPropertyInfo**ppEnum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFieldSpec`  
 [in] Especifica el `DBGPROP_INFO_FLAGS` constantes que determinan cuáles son los campos en las estructuras de propiedad enumerada de depuración que deben rellenarse.  
  
 `nRadix`  
 [in] Base para su uso en la interpretación de toda la información numérica.  
  
 `refiid`  
 [in] Se pasa este IID para filtrar el enumerador. El IID es uno de los `IDebugPropertyEnumType` interfaces que heredan de `IDebugPropertyEnumType_All`.  
  
 `ppEnum`  
 [out] Devuelve el `IEnumDebugPropertyInfo` interfaz que enumera las propiedades de miembro.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (interfaz)](../../winscript/reference/idebugproperty-interface.md)   
 [DBGPROP_INFO_FLAGS](../../winscript/reference/dbgprop-info-flags.md)   
 [IDebugPropertyEnumType_All (interfaz)](../../winscript/reference/idebugpropertyenumtype-all-interface.md)   
 [IEnumDebugPropertyInfo (Interfaz)](../../winscript/reference/ienumdebugpropertyinfo-interface.md)