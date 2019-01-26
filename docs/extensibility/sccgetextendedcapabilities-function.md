---
title: SccGetExtendedCapabilities (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b33858910c435f4dc899b24a707de06548f1c915
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54931159"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities (función)
Esta función devuelve capacidades adicionales compatibles con el complemento de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 lSccExCaps  
 [in] Una marca que especifica una funcionalidad extendida que se va a probar (vea la tabla de código de funcionalidad extendida de [marcadores de capacidad](../extensibility/capability-flags.md) para las marcas posibles).  
  
 pbSupported  
 [out] Devuelve cero (`TRUE`) si se admite la capacidad especificada; en caso contrario, devuelve cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación de capacidad get que se completó correctamente.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Error desconocido o no especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama a petición; es decir, cuando se necesita una funcionalidad que va a probarse, se llama a este método para determinar si el que se admite la capacidad. Se especifica solo un marcador a la vez.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)   
 [Marcadores de capacidad](../extensibility/capability-flags.md)