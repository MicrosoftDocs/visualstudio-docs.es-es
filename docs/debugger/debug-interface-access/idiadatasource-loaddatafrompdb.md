---
title: IDiaDataSource::loadDataFromPdb | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataFromPdb method
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 021c3ec0115267f83dbc39ba9c7c34b262fa6614
ms.sourcegitcommit: 61dc40d6c707f8c79779ec1091b296530d5a7b81
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2019
ms.locfileid: "55987384"
---
# <a name="idiadatasourceloaddatafrompdb"></a>IDiaDataSource::loadDataFromPdb
Se abre y se prepara un archivo de programa (.pdb) de la base de datos como un origen de datos de depuración.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT loadDataFromPdb (
   LPCOLESTR pdbPath
);
```

#### <a name="parameters"></a>Parámetros
pdbPath  
[in] La ruta de acceso al archivo .pdb.

## <a name="return-value"></a>Valor devuelto
Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. En la tabla siguiente se muestra los posibles valores devueltos para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_PDB_NOT_FOUND|No se pudo abrir el archivo, o puede determinar que el archivo tiene un formato no válido.|
|E_PDB_FORMAT|Se ha intentado obtener acceso a un archivo con un formato obsoleto.|
|E_INVALIDARG|Parámetro no válido.|
|E_UNEXPECTED|Ya se ha preparado el origen de datos.|

## <a name="remarks"></a>Comentarios
Este método carga los datos de depuración directamente desde un archivo. pdb.

Para validar el archivo .pdb en criterios específicos, use el [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) método.

Para obtener acceso al proceso de carga de datos (a través de un mecanismo de devolución de llamada), utilice el [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) método.

Para cargar un archivo .pdb directamente desde la memoria, utilice el [Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) método.

## <a name="example"></a>Ejemplo

```C++
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );
if (FAILED(hr))
{
    // report error
}
```

## <a name="see-also"></a>Vea también
[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)  
[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)  
[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
