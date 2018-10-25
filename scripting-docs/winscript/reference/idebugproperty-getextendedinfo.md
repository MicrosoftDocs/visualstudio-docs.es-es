---
title: IDebugProperty::GetExtendedInfo | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDebugProperty.GetExtendedInfo
apilocation:
- scrobj.dll
helpviewer_keywords:
- IDebugProperty::GetExtendedInfo
ms.assetid: a989ade5-16d5-4ee6-8d8a-8dcbfad24034
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: c66ea53bde17f2936567cd93ae0be166f35382ed
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49925548"
---
# <a name="idebugpropertygetextendedinfo"></a>IDebugProperty::GetExtendedInfo
Obtiene información de la propiedad extendida.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
HRESULT GetExtendedInfo (  
   ULONG  cInfos,  
   GUID*  rgguidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `cInfos`  
 [in] Recuento de objetos de información extendida.  
  
 `rgguidExtendedInfo`  
 [in] Una matriz de `GUID`s se pasa por lo que se pueden recuperar varios elementos de información ampliada al mismo tiempo.  
  
 `pExtendedInfo`  
 [out] Devuelve una matriz de `VARIANT`s que puede usarse para recuperar la información de la propiedad extendida.  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve un válidas `HRESULT`, normalmente `S_OK`.  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz obtiene información de este objeto extendida. La API existe solo con el fin de recuperar la información que no se presta a que se va a recuperar mediante el uso de `IDebugProperty::GetPropertyInfo`).  
  
## <a name="see-also"></a>Vea también  
 [IDebugProperty (Interfaz)](../../winscript/reference/idebugproperty-interface.md)