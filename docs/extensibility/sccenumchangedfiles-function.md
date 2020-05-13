---
title: Función SccEnumChangedFiles ? Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccEnumChangedFiles
helpviewer_keywords:
- SccEnumChangedFiles function
ms.assetid: 76cac510-107b-4c1a-ba60-9c39b6db2e71
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0b1826a87b20d6bc92254fc4a86b8e0b756400ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700905"
---
# <a name="sccenumchangedfiles-function"></a>Función SccEnumChangedFiles
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

[en] El puntero de contexto del complemento de control de código fuente.

 hWnd

[en] Identificador de la ventana IDE que el complemento de control de código fuente puede usar como elemento primario para los cuadros de diálogo que proporciona.

 cArchivos

[en] Número de nombres de `lpFileNames` archivo especificados en la matriz. También especifica el `plIsFileDifferent` tamaño de la matriz.

 lpFileNames

[en] Matriz de nombres de archivo locales que se pueden comprobar.

 plIsFileDifferent

[adentro, fuera] Matriz de valores que indica el estado de diferencia `cFiles` de cada archivo (la matriz debe tener al menos entradas). Distinto de cero significa que el archivo es diferente.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Operación completada correctamente.|
|SCC_UNSPECIFIEDERROR|Error genérico.|

## <a name="see-also"></a>Vea también
- [Funciones de API de plug-in de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
