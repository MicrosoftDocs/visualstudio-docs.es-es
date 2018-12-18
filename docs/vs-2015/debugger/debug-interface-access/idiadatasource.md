---
title: IDiaDataSource | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource interface
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 16
author: MikeJo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 33f4ca43f4cefc80508961b918e094a6954e5f3b
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51736528"
---
# <a name="idiadatasource"></a>IDiaDataSource
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Inicia el acceso a un origen de símbolos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaDataSource : IUnknown  
```  
  
## <a name="methods-in-vtable-order"></a>Métodos en orden de Vtable  
 La tabla siguiente muestran los métodos de `IDiaDataSource`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaDataSource::get_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|Recupera el nombre de archivo para el último error de carga.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Se abre y se prepara un archivo de programa (.pdb) de la base de datos como un origen de datos de depuración.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Se abre y comprueba que el archivo de programa (.pdb) de la base de datos coincide con la información de firma proporcionada; prepara el archivo .pdb como un origen de datos de depuración.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Se abre y prepara los datos de depuración asociados con el archivo.exe/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara los datos de depuración almacenados en el archivo de programa (.pdb) de la base de datos tiene acceso a través de un flujo de datos en memoria.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Se abre una sesión para consultar los símbolos.|  
  
## <a name="remarks"></a>Comentarios  
 Una llamada a uno de los métodos de carga de la `IDiaDataSource` interfaz abre el origen de símbolos. Una llamada correcta a la [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) método devuelve un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) interfaz que permite consultar el origen de datos. Si el método load devuelve un error relacionado con el archivo la [Get_lasterror](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) el método devuelve el valor contiene el nombre de archivo asociado con el error.  
  
## <a name="notes-for-callers"></a>Notas para los llamadores  
 Esta interfaz se obtiene mediante una llamada a la `CoCreateInstance` función con el identificador de clase `CLSID_DiaSource` y el identificador de interfaz de `IID_IDiaDataSource`. El ejemplo muestra cómo se obtiene esta interfaz.  
  
## <a name="example"></a>Ejemplo  
  
```cpp#  
  
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
  
 Archivo DLL: msdia80.dll  
  
## <a name="see-also"></a>Vea también  
 [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)



