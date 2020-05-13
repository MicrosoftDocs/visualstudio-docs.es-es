---
title: Función SccGetExtendedCapabilities ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccGetExtendedCapabilities
helpviewer_keywords:
- SccGetExtendedCapabilities function
ms.assetid: 588c6a92-2147-4d8b-a357-96ca7da0a092
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5247f2de7ffc63db7235f915c72b3274b8fee5f5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700724"
---
# <a name="sccgetextendedcapabilities-function"></a>Función SccGetExtendedCapabilities
Esta función devuelve capacidades adicionales admitidas por el complemento de control de código fuente.

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

[en] El puntero de contexto del complemento de control de código fuente.

 lSccExCaps

[en] Indicador que especifica una capacidad extendida para la que se va a probar (consulte la tabla Código de capacidad ampliada en [indicadores de capacidad](../extensibility/capability-flags.md) para los indicadores posibles).

 pbSupported

[fuera] Devuelve distinto de`TRUE`cero ( ) si se admite la capacidad especificada; de lo contrario, devuelve cero (`FALSE`).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La operación get capability se ha completado correctamente.|
|SCC_E_UNKNOWNERROR<br /><br /> SCC_E_NONSPECIFICERROR|Error desconocido o no especificado.|

## <a name="remarks"></a>Observaciones
 Este método se llama a petición; es decir, cuando es necesario probar una capacidad, se llama a este método para determinar si se admite esa capacidad. Solo se especifica una marca a la vez.

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Códigos de error](../extensibility/error-codes.md)
- [Banderas de capacidad](../extensibility/capability-flags.md)
