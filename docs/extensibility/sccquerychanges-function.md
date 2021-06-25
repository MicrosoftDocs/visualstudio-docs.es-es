---
description: Esta función enumera una lista determinada de archivos y proporciona información sobre los cambios de nombre de cada archivo a través de una función de devolución de llamada.
title: SccQueryChanges (Función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryChanges
helpviewer_keywords:
- SccQueryChanges function
ms.assetid: 4cd58eb3-6952-49b1-9620-8682e3eaa604
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: f93ed14671995502356ae4a19664b14bbd32ce7b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900478"
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

[in] Puntero de contexto del complemento de control de código fuente.

 nFiles

[in] Número de archivos de la `lpFileNames` matriz.

 lpFileNames

[in] Matriz de nombres de archivo sobre los que obtener información.

 pfnCallback

[in] Función de devolución de llamada para llamar a para cada nombre de archivo de la lista (vea [QUERYCHANGESFUNC para](../extensibility/querychangesfunc.md) obtener más información).

 pvCallerData

[in] Valor que se pasará sin cambios a la función de devolución de llamada.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|El proceso de consulta se completó correctamente.|
|SCC_E_PROJNOTOPEN|El proyecto no se ha abierto en el control de código fuente.|
|SCC_E_ACCESSFAILURE|Hubo un problema al acceder al sistema de control de código fuente, probablemente debido a problemas de red o contención.|
|SCC_E_NONSPECIFICERROR|Error general o no especificado.|

## <a name="remarks"></a>Observaciones
 Los cambios que se consultan son en el espacio de nombres: en concreto, cambiar el nombre, agregar y quitar un archivo.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [QUERYCHANGESFUNC](../extensibility/querychangesfunc.md)
- [Códigos de error](../extensibility/error-codes.md)
