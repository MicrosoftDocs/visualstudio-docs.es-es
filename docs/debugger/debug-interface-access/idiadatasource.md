---
title: IDiaDataSource | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 453be1d77f1d2b1759e3de4433225cf97d026054
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744911"
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicia el acceso a un origen de símbolos de depuración.

## <a name="syntax"></a>Sintaxis

```
IDiaDataSource : IUnknown
```

## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable
En la tabla siguiente se muestran los métodos de `IDiaDataSource`.

|Método|Descripción|
|------------|-----------------|
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera el nombre de archivo para el último error de carga.|
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Abre y prepara un archivo de base de datos de programa (. pdb) como un origen de datos de depuración.|
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Abre y comprueba que el archivo de base de datos de programa (. pdb) coincide con la información de firma proporcionada. prepara el archivo. pdb como un origen de datos de depuración.|
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Abre y prepara los datos de depuración asociados con el archivo. exe/. dll.|
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara los datos de depuración almacenados en un archivo de base de datos de programa (. pdb) al que se tiene acceso a través de un flujo de datos en memoria.|
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Abre una sesión para consultar los símbolos.|

## <a name="remarks"></a>Comentarios
Una llamada a uno de los métodos Load de la interfaz `IDiaDataSource` abre el origen Symbol. Una llamada correcta al método [IDiaDataSource:: openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) devuelve una interfaz [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que admite la consulta del origen de datos. Si el método Load devuelve un error relacionado con el archivo, el valor devuelto del método [IDiaDataSource:: get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) contiene el nombre de archivo asociado al error.

## <a name="notes-for-callers"></a>Notas para llamadores
Esta interfaz se obtiene llamando a la función `CoCreateInstance` con el identificador de clase `CLSID_DiaSource` y el ID. de interfaz de `IID_IDiaDataSource`. En el ejemplo se muestra cómo se obtiene esta interfaz.

## <a name="example"></a>Ejemplo

```C++

      IDiaDataSource* pSource;
HRESULT hr = CoCreateInstance(CLSID_DiaSource,
                              NULL,
                              CLSCTX_INPROC_SERVER,
                              IID_IDiaDataSource,
                              (void**) &pSource);
if (FAILED(hr))
{
    // Report error and exit
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

Biblioteca: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
