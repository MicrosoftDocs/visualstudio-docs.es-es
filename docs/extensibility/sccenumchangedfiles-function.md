---
title: SccEnumChangedFiles (función) | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: db9bc2738e9a4d7cac0d57b9c613b7070f60baff
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62802915"
---
# <a name="sccenumchangedfiles-function"></a>SccEnumChangedFiles (función)
Dada una lista de archivos locales, esta función determina qué archivos son diferentes de las versiones correspondientes en la base de datos de control de código fuente.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccEnumChangedFiles(
   LPVOID  pContext,
   HWND    hWnd,
   LONG    cFiles,
   LPCSTR* lpFileNames,
   LONG*   plIsFileDifferent
);
```

### <a name="parameters"></a>Parámetros
 pContext

[in] El puntero de contexto de complemento de control de código fuente.

 hWnd

[in] Identificador de la ventana del IDE que puede usar el complemento de control de código fuente como un elemento primario para los cuadros de diálogo que proporciona.

 cFiles

[in] Número de nombres de archivo especificado en el `lpFileNames` matriz. También especifica el tamaño de `plIsFileDifferent` matriz.

 lpFileNames

[in] Matriz de nombres de archivo local para comprobar.

 plIsFileDifferent

[in, out] Matriz de valores que indican el estado de la diferencia de cada archivo (matriz debe tener al menos `cFiles` entradas). Distinto de cero significa que el archivo es diferente.

## <a name="return-value"></a>Valor devuelto
 La implementación de complemento de control de origen de esta función debe devolver uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Operación se completó correctamente.|
|SCC_UNSPECIFIEDERROR|Error genérico.|

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)