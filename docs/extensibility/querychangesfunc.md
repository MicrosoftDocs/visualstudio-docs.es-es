---
title: QUERYCHANGESFUNC | Microsoft Docs
description: La función de devolución de llamada QUERYCHANGESFUNC se usa para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
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
ms.openlocfilehash: b061fbfb6644f77348574020c0a5cb614691ae6b
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2021
ms.locfileid: "112899139"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Se trata de una función de devolución de llamada que usa la operación [SccQueryChanges](../extensibility/sccquerychanges-function.md) para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.

 A `SccQueryChanges` la función se le da una lista de archivos y un puntero a la `QUERYCHANGESFUNC` devolución de llamada. El complemento de control de código fuente enumera la lista dada y proporciona el estado (a través de esta devolución de llamada) para cada archivo de la lista.

## <a name="signature"></a>Firma

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

[in] Parámetro `pvCallerData` pasado por el autor de la llamada (el IDE) a [SccQueryChanges.](../extensibility/sccquerychanges-function.md) El complemento de control de código fuente no debe realizar suposiciones sobre el contenido de este valor.

 pChangesData

[in] Puntero a una [estructura QUERYCHANGESDATA structure](#LinkQUERYCHANGESDATA) que describe los cambios en un archivo.

## <a name="return-value"></a>Valor devuelto
 El IDE devuelve un código de error adecuado:

|Valor|Descripción|
|-----------|-----------------|
|SCC_OK|Continúe el procesamiento.|
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|
|SCC_E_xxx|Cualquier error SCC adecuado debe detener el procesamiento.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a> QUERYCHANGESDATA (estructura)
 La estructura que se pasa para cada archivo es similar a la siguiente:

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

 dwSize Tamaño de esta estructura (en bytes).

 lpFileName El nombre de archivo original para este elemento.

 DwChangeType Code que indica el estado del archivo:

|Código|Descripción|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|No se puede saber qué ha cambiado.|
|`SCC_CHANGE_UNCHANGED`|No hay cambios de nombre para este archivo.|
|`SCC_CHANGE_DIFFERENT`|Archivo con una identidad diferente, pero el mismo nombre existe en la base de datos.|
|`SCC_CHANGE_NONEXISTENT`|El archivo no existe en la base de datos ni localmente.|
|`SCC_CHANGE_DATABASE_DELETED`|Archivo eliminado en la base de datos.|
|`SCC_CHANGE_LOCAL_DELETED`|El archivo se eliminó localmente, pero el archivo todavía existe en la base de datos. Si no se puede determinar, devuelva `SCC_CHANGE_DATABASE_ADDED` .|
|`SCC_CHANGE_DATABASE_ADDED`|Archivo agregado a la base de datos, pero no existe localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|El archivo no existe en la base de datos y es un nuevo archivo local.|
|`SCC_CHANGE_RENAMED_TO`|Se ha cambiado el nombre del archivo o se ha movido a la base de datos como `lpLatestName` .|
|`SCC_CHANGE_RENAMED_FROM`|Se ha cambiado el nombre del archivo o se ha movido en la base de datos de ; si es demasiado costoso de realizar el seguimiento, devuelva una `lpLatestName` marca diferente, como `SCC_CHANGE_DATABASE_ADDED` .|

 lpLatestName Nombre de archivo actual para este elemento.

## <a name="see-also"></a>Consulta también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Códigos de error](../extensibility/error-codes.md)
