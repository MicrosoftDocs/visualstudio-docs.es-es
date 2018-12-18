---
title: IDebugExtendedProperty::GetExtendedPropertyInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugExtendedProperty.GetExtendedPropertyInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugExtendedProperty::GetExtendedPropertyInfo
ms.assetid: 56edf538-5082-4653-82b6-e6640d6f61ba
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: f314a9c777eef1716a382c74b9ea250846542da7
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49935479"
---
# <a name="idebugextendedpropertygetextendedpropertyinfo"></a>IDebugExtendedProperty::GetExtendedPropertyInfo
Captura información extendida de una propiedad extendida, que es más información que el más sencillo `IDebugProperty`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetExtendedPropertyInfo(  
   EX_DBGPROP_INFO_FLAGS  dwFieldSpec,  
   UINT  nRadix,  
   ExtendedDebugPropertyInfo*  pExtendedPropertyInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `dwFieldSpec`  
 [in] Especifica las constantes EX_DBGPROP_INFO_FLAGS que determinan los campos que se pueden rellenar en el `ExtendedDebugPropertyInfo` estructura.  
  
 `nRadix`  
 [in] Base para su uso en la interpretación de toda la información numérica.  
  
 `pExtendedPropertyInfo`  
 [out] Devuelve el `ExtendedDebugPropertyInfo` estructura que describe la propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="see-also"></a>Vea también  
 [IDebugExtendedProperty (interfaz)](../../winscript/reference/idebugextendedproperty-interface.md)   
 [EX_DBGPROP_INFO_FLAGS](../../winscript/reference/ex-dbgprop-info-flags.md)   
 [ExtendedDebugPropertyInfo (Estructura)](../../winscript/reference/extendeddebugpropertyinfo-structure.md)