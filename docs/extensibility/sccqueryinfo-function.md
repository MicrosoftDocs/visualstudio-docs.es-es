---
title: Función SccQueryInfo | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccQueryInfo
helpviewer_keywords:
- SccQueryInfo function
ms.assetid: 3973d336-a9b7-41a2-a4e6-bb8184a96aaf
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 5807eb6b695e140350696436a8bba351687f4a24
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72720831"
---
# <a name="sccqueryinfo-function"></a>SccQueryInfo (Función)
Esta función obtiene información de estado de un conjunto de archivos seleccionados bajo control de código fuente.

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

de Estructura de contexto del complemento de control de código fuente.

 N archivos

de Número de archivos especificados en la matriz de `lpFileNames` y la longitud de la matriz de `lpStatus`.

 lpFileNames

de Matriz de nombres de los archivos que se van a consultar.

 lpStatus

[in, out] Matriz en la que el complemento de control de código fuente devuelve las marcas de estado de cada archivo. Para obtener más información, consulte el [código de estado de archivo](../extensibility/file-status-code-enumerator.md).

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|La consulta se realizó correctamente.|
|SCC_E_ACCESSFAILURE|Hubo un problema con el acceso al sistema de control de código fuente, probablemente debido a problemas de red o de contención. Se recomienda un reintento.|
|SCC_E_PROJNOTOPEN|El proyecto no está abierto bajo control de código fuente.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Comentarios
 Si `lpFileName` es una cadena vacía, actualmente no hay información de estado para actualizar. De lo contrario, es el nombre completo de la ruta de acceso del archivo para el que puede haber cambiado la información de estado.

 La matriz devuelta puede ser una máscara de bits de `SCC_STATUS_xxxx` bits. Para obtener más información, consulte el [código de estado de archivo](../extensibility/file-status-code-enumerator.md). Es posible que un sistema de control de código fuente no admita todos los tipos de bits. Por ejemplo, si no se ofrece `SCC_STATUS_OUTOFDATE`, no se establece el bit.

 Al usar esta función para desproteger archivos, tenga en cuenta los siguientes requisitos de estado de `MSSCCI`:

- `SCC_STATUS_OUTBYUSER` se establece cuando el usuario actual ha desprotegido el archivo.

- no se puede establecer `SCC_STATUS_CHECKEDOUT` a menos que se establezca `SCC_STATUS_OUTBYUSER`.

- `SCC_STATUS_CHECKEDOUT` solo se establece cuando el archivo se desprotege en el directorio de trabajo designado.

- Si el usuario actual Desprotege el archivo en un directorio distinto del directorio de trabajo, se establece `SCC_STATUS_OUTBYUSER` pero `SCC_STATUS_CHECKEDOUT` no.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Código de estado de archivo](../extensibility/file-status-code-enumerator.md)