---
title: Función SccUninitialize | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccUninitialize
helpviewer_keywords:
- SccUninitialize function
ms.assetid: 17cf5337-d251-4422-bc96-93fe7d48f2ae
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 321f50173e3c1517cc6a431ff74933e1a02ef1d0
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720131"
---
# <a name="sccuninitialize-function"></a>SccUninitialize (Función)
Esta función limpia las asignaciones o conexiones abiertas creadas por una llamada anterior a [SccInitialize](../extensibility/sccinitialize-function.md) como preparación para cerrar el complemento de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccUninitialize (
   LPVOID pvContext
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

de Puntero a la estructura de contexto del complemento de control de código fuente creada en [SccInitialize](../extensibility/sccinitialize-function.md).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La limpieza se completó correctamente.|

## <a name="remarks"></a>Comentarios
 El complemento de control de código fuente es responsable de preparar su cierre y liberar memoria que el complemento ha asignado para la estructura de contexto. Se llama a la función una vez para cada instancia determinada de un complemento. Una llamada a [SccInitialize](../extensibility/sccinitialize-function.md) precede a esta llamada. Todavía no puede haber ningún proyecto abierto en el momento de la llamada a `SccUninitialize`.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [SccInitialize](../extensibility/sccinitialize-function.md)