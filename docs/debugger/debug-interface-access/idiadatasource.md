---
title: IDiaDataSource | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 48e248e537749983293bbeefd60098eabcf70b2d
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="idiadatasource"></a>IDiaDataSource
Inicia el acceso a un origen de símbolos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaDataSource`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera el nombre de archivo para el último error de carga.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Se abre y se prepara un archivo de programa (.pdb) de la base de datos como un origen de datos de depuración.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Se abre y comprueba que el archivo de programa (.pdb) de la base de datos coincide con la información de firma proporcionada; prepara el archivo .pdb como un origen de datos de depuración.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Se abre y prepara los datos de depuración asociados con el archivo.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara los datos de depuración almacenados en el archivo programa (.pdb) de la base de datos tiene acceso a través de un flujo de datos en memoria.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Se abre una sesión para consultar los símbolos.|  
  
## <a name="remarks"></a>Comentarios  
 Una llamada a uno de los métodos de carga de la `IDiaDataSource` interfaz abre el origen de símbolos. Una llamada correcta a la [idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) método devuelve un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaz que permite consultar el origen de datos. Si el método de carga devuelve un error relacionado con el archivo la [idiadatasource:: Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) método devuelve el valor contiene el nombre de archivo asociado con el error.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se obtiene mediante una llamada a la `CoCreateInstance` función con el identificador de clase `CLSID_DiaSource` y el identificador de interfaz de `IID_IDiaDataSource`. En el ejemplo se muestra cómo se obtiene esta interfaz.  
  
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
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)