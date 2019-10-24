---
title: IDiaDataSource::loadDataForExe | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 7a86abb00ebc090c37f03a5533376ae0b9c3e8ae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72744957"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Abre y prepara los datos de depuración asociados con el archivo. exe/. dll.

## <a name="syntax"></a>Sintaxis

```C++
HRESULT loadDataForExe (
   LPCOLESTR executable,
   LPCOLESTR searchPath,
   IUnknown* pCallback
);
```

#### <a name="parameters"></a>Parámetros
ejecutable

de Ruta de acceso al archivo. exe o. dll.

searchPath

de Ruta de acceso alternativa para buscar datos de depuración.

pCallback

de Interfaz `IUnknown` para un objeto que admite una interfaz de devolución de llamada de depuración, como [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)y/o las interfaces [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .

## <a name="return-value"></a>Valor devuelto
Si se realiza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error. En la tabla siguiente se muestran algunos de los códigos de error posibles para este método.

|Valor|Descripción|
|-----------|-----------------|
|E_PDB_NOT_FOUND|No se pudo abrir el archivo o el archivo tiene un formato no válido.|
|E_PDB_FORMAT|Se intentó obtener acceso a un archivo con un formato obsoleto.|
|E_PDB_INVALID_SIG|La firma no coincide.|
|E_PDB_INVALID_AGE|Age no coincide.|
|E_INVALIDARG|Parámetro no válido.|
|E_UNEXPECTED|El origen de datos ya se ha preparado.|

## <a name="remarks"></a>Comentarios
El encabezado de depuración del archivo. exe/. dll nombra la ubicación de los datos de depuración asociada.

Este método lee el encabezado de depuración y, a continuación, busca y prepara los datos de depuración. Es posible que el progreso de la búsqueda, de manera opcional, se notifique y controle mediante devoluciones de llamada. Por ejemplo, se invoca [IDiaLoadCallback:: NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) cuando el método `IDiaDataSource::loadDataForExe` busca y procesa un directorio de depuración.

Las interfaces [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) y [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) permiten a la aplicación cliente proporcionar métodos alternativos para leer datos del archivo ejecutable cuando no se puede tener acceso al archivo directamente mediante el estándar. e/s de archivos.

Para cargar un archivo. pdb sin validación, use el método [IDiaDataSource:: loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .

Para validar el archivo. pdb con criterios concretos, use el método [IDiaDataSource:: loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .

Para cargar un archivo. pdb directamente desde la memoria, use el método [IDiaDataSource:: loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .

## <a name="example"></a>Ejemplo

```C++
class MyCallBack: public IDiaLoadCallback
{
...
};
MyCallBack callback;
...
HRESULT hr = pSource->loadDataForExe( L"myprog.exe", L".\debug", (IUnknown*)&callback);
if (FAILED(hr))
{
    // Report error
}
```

## <a name="see-also"></a>Vea también
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)
- [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)
- [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)
- [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)
- [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)
- [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)
- [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)
- [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)
