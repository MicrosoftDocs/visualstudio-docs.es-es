---
description: Esta función determina si el complemento de control de código fuente admite la creación de MSSCCPRJ. Archivo SCC para cada uno de los archivos dados.
title: Función SccWillCreateSccFile | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- SccWillCreateSccFile
helpviewer_keywords:
- SccWillCreateSccFile function
ms.assetid: 0d7542f0-4351-41b3-b24c-960ab99c05a1
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 9f9e6df29b9f44d852c7c84488a3febf590fcc0e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112900452"
---
# <a name="sccwillcreatesccfile-function"></a>SccWillCreateSccFile (Función)
Esta función determina si el complemento de control de código fuente admite la creación de MSSCCPRJ. Archivo SCC para cada uno de los archivos dados.

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

[in] Puntero de contexto del complemento de control de código fuente.

 nFiles

[in] Número de nombres de archivo incluidos en la `lpFileNames` matriz, así como la longitud de la `pbSccFiles` matriz.

 lpFileNames

[in] Matriz de nombres de archivo completos para comprobar (el autor de la llamada debe asignar la matriz).

 pbSccFiles

[in, out] Matriz en la que se almacenarán los resultados.

## <a name="return-value"></a>Valor devuelto
 Se espera que la implementación del complemento de control de código fuente de esta función devuelva uno de los valores siguientes:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Correcto.|
|SCC_E_INVALIDFILEPATH|Una de las rutas de acceso de la matriz no es válida.|
|SCC_E_NONSPECIFICERROR|Error no específico.|

## <a name="remarks"></a>Observaciones
 Se llama a esta función con una lista de archivos para determinar si el complemento de control de código fuente proporciona compatibilidad con MSSCCPRJ. Archivo SCC para cada uno de los archivos dados (para obtener más información sobre MSSCCPRJ. Archivo SCC, consulte [MSSCCPRJ. Archivo SCC](../extensibility/mssccprj-scc-file.md)). Los complementos de control de código fuente pueden declarar si tienen la capacidad de crear MSSCCPRJ. Archivos SCC declarando durante `SCC_CAP_SCCFILE` la inicialización. El complemento devuelve o por archivo en la matriz para indicar cuál de `TRUE` los archivos `FALSE` `pbSccFiles` dados tiene MSSCCPRJ. Compatibilidad con SCC. Si el complemento devuelve un código correcto de la función , se respetan los valores de la matriz de valor devuelto. En caso de error, se omite la matriz.

## <a name="see-also"></a>Consulta también
- [Funciones de API de complemento de control de código fuente](../extensibility/source-control-plug-in-api-functions.md)
- [Archivo MSSCCPRJ.SCC](../extensibility/mssccprj-scc-file.md)
