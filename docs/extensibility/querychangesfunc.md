---
title: QUERYCHANGESFUNC | Microsoft Docs
description: La función de devolución de llamada QUERYCHANGESFUNC se usa para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cc797d68f6df6d9aab93554ba95955a7d9f45eea
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2021
ms.locfileid: "105068627"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Se trata de una función de devolución de llamada que usa la operación [SccQueryChanges](../extensibility/sccquerychanges-function.md) para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.

 A la `SccQueryChanges` función se le asigna una lista de archivos y un puntero a la `QUERYCHANGESFUNC` devolución de llamada. El complemento de control de código fuente enumera la lista especificada y proporciona el estado (a través de esta devolución de llamada) para cada archivo de la lista.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

de `pvCallerData` Parámetro pasado por el llamador (el IDE) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). El complemento de control de código fuente no debe hacer suposiciones sobre el contenido de este valor.

 pChangesData

de Puntero a una estructura de [estructura QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) que describe los cambios en un archivo.

## <a name="return-value"></a>Valor devuelto
 El IDE devuelve un código de error adecuado:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Continúe el procesamiento.|
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|
|SCC_E_xxx|Cualquier error de SCC adecuado debe detener el procesamiento.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> Estructura QUERYCHANGESDATA
 La estructura que se pasa para cada archivo tiene el aspecto siguiente:

```cpp
struct QUERYCHANGESDATA_A
{
    DWORD  dwSize;
    LPCSTR lpFileName;
    DWORD  dwChangeType;
    LPCSTR lpLatestName;
};

typedef struct QUERYCHANGESDATA_A QUERYCHANGESDATA;

struct QUERYCHANGESDATA_W
{
    DWORD   dwSize;
    LPCWSTR lpFileName;
    DWORD   dwChangeType;
    LPCWSTR lpLatestName;
};
```

 Tamaño de dwSize de esta estructura (en bytes).

 lpFileName el nombre de archivo original de este elemento.

 Código de dwChangeType que indica el estado del archivo:

|Código|Descripción|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|No se puede saber qué ha cambiado.|
|`SCC_CHANGE_UNCHANGED`|No cambia el nombre de este archivo.|
|`SCC_CHANGE_DIFFERENT`|Archivo con una identidad diferente, pero existe el mismo nombre en la base de datos.|
|`SCC_CHANGE_NONEXISTENT`|El archivo no existe en la base de datos o localmente.|
|`SCC_CHANGE_DATABASE_DELETED`|Archivo eliminado en la base de datos.|
|`SCC_CHANGE_LOCAL_DELETED`|El archivo se eliminó localmente, pero el archivo sigue existiendo en la base de datos. Si no se puede determinar, devuelve `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Archivo agregado a la base de datos, pero que no existe localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|El archivo no existe en la base de datos y es un nuevo archivo local.|
|`SCC_CHANGE_RENAMED_TO`|Archivo cuyo nombre se ha cambiado o se ha pasado en la base de datos como `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Archivo al que se cambia el nombre o se mueve en la base de datos de `lpLatestName` ; si es demasiado caro realizar el seguimiento, devuelve una marca diferente, como `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName el nombre de archivo actual para este elemento.

## <a name="see-also"></a>Consulte también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Códigos de error](../extensibility/error-codes.md)
