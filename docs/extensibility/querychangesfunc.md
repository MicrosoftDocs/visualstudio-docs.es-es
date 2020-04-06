---
title: QUERYCHANGESFUNC Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- QUERYCHANGESFUNC
helpviewer_keywords:
- QUERYCHANGESFUNC callback function
- QUERYCHANGESDATA structure
ms.assetid: 9d383e2c-eee1-4996-973a-0652d4c5951c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30864cae95672f4026084a94c5474d165b124cba
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701636"
---
# <a name="querychangesfunc"></a>QUERYCHANGESFUNC
Se trata de una función de devolución de llamada utilizada por la operación [SccQueryChanges](../extensibility/sccquerychanges-function.md) para enumerar una colección de nombres de archivo y determinar el estado de cada archivo.

 A `SccQueryChanges` la función se le da `QUERYCHANGESFUNC` una lista de archivos y un puntero a la devolución de llamada. El complemento de control de código fuente enumera la lista dada y proporciona el estado (a través de esta devolución de llamada) para cada archivo de la lista.

## <a name="signature"></a>Signature

```cpp
typedef BOOL (*QUERYCHANGESFUNC)(
   LPVOID pvCallerData,
   QUERYCHANGESDATA * pChangesData
);
```

## <a name="parameters"></a>Parámetros
 pvCallerData

[en] Parámetro `pvCallerData` pasado por el llamador (el IDE) a [SccQueryChanges](../extensibility/sccquerychanges-function.md). El complemento de control de código fuente no debe hacer ninguna suposición sobre el contenido de este valor.

 pChangesData

[en] Puntero a una estructura [QUERYCHANGESDATA](#LinkQUERYCHANGESDATA) que describe los cambios en un archivo.

## <a name="return-value"></a>Valor devuelto
 El IDE devuelve un código de error adecuado:

|Value|Descripción|
|-----------|-----------------|
|SCC_OK|Continúe el procesamiento.|
|SCC_I_OPERATIONCANCELED|Detiene el procesamiento.|
|SCC_E_xxx|Cualquier error SCC apropiado debe detener el procesamiento.|

## <a name="querychangesdata-structure"></a><a name="LinkQUERYCHANGESDATA"></a>Estructura QUERYCHANGESDATA
 La estructura pasada para cada archivo tiene el siguiente aspecto:

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

 dwChangeType Código que indica el estado del archivo:

|Código|Descripción|
|----------|-----------------|
|`SCC_CHANGE_UNKNOWN`|No puedo decir lo que ha cambiado.|
|`SCC_CHANGE_UNCHANGED`|No hay cambios de nombre para este archivo.|
|`SCC_CHANGE_DIFFERENT`|Archivo con una identidad diferente, pero el mismo nombre existe en la base de datos.|
|`SCC_CHANGE_NONEXISTENT`|El archivo no existe ni en la base de datos ni localmente.|
|`SCC_CHANGE_DATABASE_DELETED`|Archivo eliminado en la base de datos.|
|`SCC_CHANGE_LOCAL_DELETED`|Archivo eliminado localmente, pero el archivo sigue existiendo en la base de datos. Si esto no se `SCC_CHANGE_DATABASE_ADDED`puede determinar, devuelva .|
|`SCC_CHANGE_DATABASE_ADDED`|Archivo agregado a la base de datos pero no existe localmente.|
|`SCC_CHANGE_LOCAL_ADDED`|El archivo no existe en la base de datos y es un nuevo archivo local.|
|`SCC_CHANGE_RENAMED_TO`|Archivo renombrado o movido en `lpLatestName`la base de datos como .|
|`SCC_CHANGE_RENAMED_FROM`|Archivo renombrado o movido en `lpLatestName`la base de datos desde ; si esto es demasiado caro de rastrear, `SCC_CHANGE_DATABASE_ADDED`devuelva una bandera diferente, como .|

 lpLatestName El nombre de archivo actual para este elemento.

## <a name="see-also"></a>Vea también
- [Funciones de devolución de llamada implementadas por el IDE](../extensibility/callback-functions-implemented-by-the-ide.md)
- [SccQueryChanges](../extensibility/sccquerychanges-function.md)
- [Códigos de error](../extensibility/error-codes.md)
