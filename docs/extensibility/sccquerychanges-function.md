---
title: Función SccQueryChanges (SccQueryChanges) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ec335d808c287decb75bf759d5a3795d98962579
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700493"
---
# <a name="sccquerychanges-function"></a>SccQueryChanges (Función)
Esta función enumera una lista determinada de archivos, proporcionando información sobre los cambios de nombre para cada archivo a través de una función de devolución de llamada.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccQueryChanges(
   LPVOID           pContext,
   LONG             nFiles,
   LPCSTR*          lpFileNames,
   QUERYCHANGESFUNC pfnCallback,
   LPVOID           pvCallerData
);
```

#### <a name="parameters"></a>Parámetros
 pContext

[en] El puntero de contexto del complemento de control de código fuente.

 nArchivos

[en] Número de `lpFileNames` archivos en la matriz.

 lpFileNames

[en] Matriz de nombres de archivo para obtener información sobre.

 pfnCallback

[en] Función de devolución de llamada para llamar a cada nombre de archivo de la lista (consulte [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md) para obtener más información).

 pvCallerData

[en] Valor que se pasará sin cambios a la función de devolución de llamada.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|El proceso de consulta se completó correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto en el control de código fuente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_NONSPECIFICERROR|Se ha producido un error general o no especificado.|

## <a name="remarks"></a>Observaciones
 Los cambios que se consultan se realizan en el espacio de nombres: específicamente, cambiar el nombre, agregar y quitar un archivo.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Códigos de error](../extensibility/error-codes.md)
