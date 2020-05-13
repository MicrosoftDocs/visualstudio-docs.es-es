---
title: Función SccWillCreateSccFile ( SccWillCreateSccFile) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0694fd6b4ba82faf8b05354765fc5734efe2ef4d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700210"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (Función)
Esta función determina si el complemento de control de código fuente admite la creación de MSSCCPRJ. SCC para cada uno de los archivos especificados.

## <a name="syntax"></a>Sintaxis

```cpp
SCCRTN SccWillCreateSccFile(
   LPVOID  pContext,
   LONG    nFiles,
   LPCSTR* lpFileNames,
   LPBOOL  pbSccFiles
);
```

#### <a name="parameters"></a>Parámetros
 pContext

[en] El puntero de contexto del complemento de control de código fuente.

 nArchivos

[en] El número de nombres `lpFileNames` de archivo incluidos en `pbSccFiles` la matriz, así como la longitud de la matriz.

 lpFileNames

[en] Una matriz de nombres de archivo completos para comprobar (la matriz debe ser asignada por el autor de la llamada).

 pbSccFiles

[adentro, fuera] Matriz en la que almacenar los resultados.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los siguientes valores:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|
|SCC_E_NONSPECIFICERROR|Fallo inespecífico.|

## <a name="remarks"></a>Observaciones
 Esta función se llama con una lista de archivos para determinar si el complemento de control de código fuente proporciona soporte en MSSCCPRJ. SCC para cada uno de los archivos dados (para más información sobre el MSSCCPRJ. SCC, consulte [MSSCCPRJ. SCC](../extensibility/mssccprj-scc-file.md)). Los complementos de control de código fuente pueden declarar si tienen la capacidad de crear MSSCCPRJ. SCC declarando `SCC_CAP_SCCFILE` durante la inicialización. El plug-in `TRUE` `FALSE` devuelve o `pbSccFiles` por archivo en la matriz para indicar cuál de los archivos dados tiene MSSCCPRJ. Soporte SCC. Si el complemento devuelve un código de éxito de la función, se respetan los valores de la matriz return. En caso de error, se omite la matriz.

## <a name="see-also"></a>Vea también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
