---
description: Esta función obtiene información de estado para un conjunto de archivos seleccionados bajo control de código fuente.
title: Función SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 369bbd8d783e5d33ea1519b7ad8a4a37476dc62b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904144"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo (Función)
Esta función obtiene información de estado para un conjunto de archivos seleccionados bajo control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccQueryInfo(
   LPVOID  pvContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPLONG  lpStatus
);
```

#### <a name="parameters"></a>Parámetros
 pvContext

[in] Estructura de contexto del complemento de control de código fuente.

 nFiles

[in] Número de archivos especificados en la `lpFileNames` matriz y la longitud de la `lpStatus` matriz.

 lpFileNames

[in] Matriz de nombres de archivos que se consultarán.

 lpStatus

[in, out] Matriz en la que el complemento de control de código fuente devuelve las marcas de estado de cada archivo. Para obtener más información, vea [Código de estado de archivo](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La consulta se ha realizado correctamente.|
|SCC_E_ACCESSFAILURE|Hubo un problema con el acceso al sistema de control de código fuente, probablemente causado por problemas de red o contención. Se recomienda un reintento.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Si `lpFileName` es una cadena vacía, actualmente no hay información de estado que actualizar. De lo contrario, es el nombre de ruta de acceso completo del archivo para el que puede haber cambiado la información de estado.

 La matriz de devolución puede ser una máscara de `SCC_STATUS_xxxx` bits de bits. Para obtener más información, vea [Código de estado de archivo](../extensibility/file-status-code-enumerator.md). Es posible que un sistema de control de código fuente no admita todos los tipos de bits. Por ejemplo, si `SCC_STATUS_OUTOFDATE` no se ofrece, el bit no se establece.

 Al usar esta función para desalar archivos, tenga en cuenta los siguientes requisitos `MSSCCI` de estado:

- `SCC_STATUS_OUTBYUSER` se establece cuando el usuario actual ha desprotegiendo el archivo.

- `SCC_STATUS_CHECKEDOUT` no se puede establecer a menos `SCC_STATUS_OUTBYUSER` que se establezca .

- `SCC_STATUS_CHECKEDOUT` solo se establece cuando el archivo se desprotegía en el directorio de trabajo designado.

- Si el usuario actual desprotegía el archivo en un directorio distinto del directorio de trabajo, se `SCC_STATUS_OUTBYUSER` establece pero no lo `SCC_STATUS_CHECKEDOUT` está.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)
