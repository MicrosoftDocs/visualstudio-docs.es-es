---
description: Esta función enumera una lista determinada de archivos y proporciona información sobre los cambios de nombre de cada archivo a través de una función de devolución de llamada.
title: Función SccQueryChanges | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e34c37ca999b05e7148d910032fe90c33470ce50
ms.sourcegitcommit: f33ca1fc99f5d9372166431cefd0e0e639d20719
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2021
ms.locfileid: "102220526"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges (Función)
Esta función enumera una lista determinada de archivos y proporciona información sobre los cambios de nombre de cada archivo a través de una función de devolución de llamada.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parámetros
 pContext

de Puntero de contexto del complemento de control de código fuente.

 N archivos

de Número de archivos de la `lpFileNames` matriz.

 lpFileNames

de Matriz de nombres de archivo de los que se va a obtener información.

 pfnCallback

de Función de devolución de llamada a la que se llama para cada nombre de archivo de la lista (vea [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obtener más información).

 pvCallerData

de Valor que se pasará sin modificar a la función de devolución de llamada.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El proceso de consulta se completó correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto en el control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al obtener acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención.|
|SCC_E_NONSPECIFICERROR|Se produjo un error no especificado o general.|

## <a name="remarks"></a>Observaciones
 Los cambios que se están consultando son el espacio de nombres: específicamente, el cambio de nombre, la adición y la eliminación de un archivo.

## <a name="see-also"></a>Consulte también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Códigos de error](../extensibility/error-codes.md)
