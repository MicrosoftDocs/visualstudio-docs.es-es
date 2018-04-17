---
title: Función SccGetExtendedCapabilities | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 46ae3e051028e8239be5949500ebb710d67eee17
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities (función)
Esta función devuelve funcionalidades adicionales compatibles con el complemento de control de código fuente.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
SCCRTN SccGetExtendedCapabilities(  
   LPVOID pContext,  
   LONG lSccExCaps,  
   LPBOOL pbSupported  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 pContext  
 [in] El puntero de contexto de complemento de control de código fuente.  
  
 lSccExCaps  
 [in] Un indicador que especifica una capacidad ampliada para la que se va a probar (vea la tabla de código de funcionalidad extendida de [capacidad marcas](../extensibility/capability-flags.md) para las marcas posibles).  
  
 pbSupported  
 [out] Devuelve distinto de cero (`TRUE`) si se admite la capacidad especificada; en caso contrario, devuelve cero (`FALSE`).  
  
## <a name="return-value"></a>Valor devuelto  
 La implementación de complemento de control de origen de esta función debe devolver uno de los siguientes valores:  
  
|Valor|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación de capacidad de get finalizada correctamente.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Error desconocido o no especificado.|  
  
## <a name="remarks"></a>Comentarios  
 Este método se llama a petición; es decir, cuando se necesita una capacidad va a probar, se llama a este método para determinar si el que se admite la capacidad. Se especifica solo un marcador a la vez.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de API de complemento de Control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)   
 [Marcadores de capacidad](../extensibility/capability-flags.md)