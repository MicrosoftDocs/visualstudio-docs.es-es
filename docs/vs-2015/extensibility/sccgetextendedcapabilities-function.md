---
title: Función SccGetExtendedCapabilities | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
caps.latest.revision: 17
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f02591eac6a3f69ae5513aa9dc0abed381cd1c8a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68200106"
---
# <a name="sccgetextendedcapabilities-function"></a>SccGetExtendedCapabilities (Función)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta función devuelve capacidades adicionales que admite el complemento de control de código fuente.  
  
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
 de Puntero de contexto del complemento de control de código fuente.  
  
 lSccExCaps  
 de Una marca que especifica una capacidad extendida que se va a probar (vea la tabla de códigos de funcionalidad extendida en [marcas de capacidad](../extensibility/capability-flags.md) para las posibles marcas).  
  
 pbSupported  
 enuncia Devuelve un valor distinto de cero ( `TRUE` ) si se admite la capacidad especificada; de lo contrario, devuelve cero ( `FALSE` ).  
  
## <a name="return-value"></a>Valor devuelto  
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:  
  
|Value|Descripción|  
|-----------|-----------------|  
|SCC_OK|La operación de obtención de capacidad se completó correctamente.|  
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Se produjo un error desconocido o no especificado.|  
  
## <a name="remarks"></a>Observaciones  
 Este método se llama a petición; es decir, cuando es necesario probar una funcionalidad, se llama a este método para determinar si se admite esa capacidad. Solo se especifica una marca a la vez.  
  
## <a name="see-also"></a>Consulte también  
 [Funciones de la API del complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)   
 [Códigos de error](../extensibility/error-codes.md)   
 [Marcas de capacidad](../extensibility/capability-flags.md)
