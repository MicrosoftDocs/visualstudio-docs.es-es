---
title: Función SccQueryInfo ( SccQueryInfo) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 1efae18f15588f4dacf3409ea95e30af05397c6e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700478"
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

[en] La estructura de contexto del complemento de control de código fuente.

 nArchivos

[en] Número de archivos especificados en la `lpFileNames` `lpStatus` matriz y la longitud de la matriz.

 lpFileNames

[en] Matriz de nombres de archivos que se van a consultar.

 lpStatus

[adentro, fuera] Matriz en la que el complemento de control de código fuente devuelve los indicadores de estado de cada archivo. Para obtener más información, consulte Código de [estado de](../extensibility/file-status-code-enumerator.md)archivo .

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|La consulta se realizó correctamente.|
|SCC_E_ACCESSFAILURE|Se ha producido un problema con el acceso al sistema de control de código fuente, probablemente causado por problemas de red o contención. Se recomienda un reintento.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Si `lpFileName` es una cadena vacía, actualmente no hay información de estado que actualizar. De lo contrario, es el nombre de ruta de acceso completo del archivo para el que puede haber cambiado la información de estado.

 La matriz return puede ser `SCC_STATUS_xxxx` una máscara de bits. Para obtener más información, consulte Código de [estado de](../extensibility/file-status-code-enumerator.md)archivo . Es posible que un sistema de control de código fuente no admita todos los tipos de bits. Por ejemplo, `SCC_STATUS_OUTOFDATE` si no se ofrece, el bit simplemente no se establece.

 Cuando utilice esta función para desproteger archivos, tenga en cuenta los siguientes `MSSCCI` requisitos de estado:

- `SCC_STATUS_OUTBYUSER`se establece cuando el usuario actual ha traído el archivo.

- `SCC_STATUS_CHECKEDOUT`no se `SCC_STATUS_OUTBYUSER` puede establecer a menos que se establezca.

- `SCC_STATUS_CHECKEDOUT`sólo se establece cuando el archivo se desprotege en el directorio de trabajo designado.

- Si el usuario actual desprotege el archivo en un `SCC_STATUS_OUTBYUSER` directorio distinto `SCC_STATUS_CHECKEDOUT` del directorio de trabajo, se establece, pero no.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)
