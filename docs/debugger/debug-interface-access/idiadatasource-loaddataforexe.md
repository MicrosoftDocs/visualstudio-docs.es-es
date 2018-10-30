---
title: Loaddataforexe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaDataSource::loadDataForExe method
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 32c5c3850eaeb1ce7e97fdeb2473fb707e66be1d
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49880023"
---
# <a name="idiadatasourceloaddataforexe"></a>IDiaDataSource::loadDataForExe
Se abre y prepara los datos de depuración asociados con el archivo.exe/.dll.  
  
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
 [in] Ruta de acceso al archivo .exe o .dll.  
  
 searchPath  
 [in] Ruta de acceso alternativo para buscar datos de depuración.  
  
 pCallback  
 [in] Un `IUnknown` interfaz para un objeto que admite una interfaz de devolución de llamada de depuración, como la [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), o [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaces.  
  
## <a name="return-value"></a>Valor devuelto  
 Si es correcto, devuelve `S_OK`; en caso contrario, devuelve un código de error. La siguiente tabla muestra algunos de los códigos de error posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E_PDB_NOT_FOUND|No se pudo abrir el archivo o el archivo tiene un formato no válido.|  
|E_PDB_FORMAT|Se ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E_PDB_INVALID_SIG|Firma no coincide.|  
|E_PDB_INVALID_AGE|Edad no coincide.|  
|E_INVALIDARG|Parámetro no válido.|  
|E_UNEXPECTED|Ya se ha preparado el origen de datos.|  
  
## <a name="remarks"></a>Comentarios  
 El encabezado de depuración del archivo.exe/.dll nombres de la ubicación de datos de depuración.  
  
 Este método lee el encabezado de depuración y, a continuación, busca y prepara los datos de depuración. El progreso de la búsqueda si lo desea, puede, se notifica y controla a través de las devoluciones de llamada. Por ejemplo, el [Idialoadcallback](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) se invoca cuando el `IDiaDataSource::loadDataForExe` método busca y procesa un directorio de depuración.  
  
 El [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) y [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) interfaces permiten la aplicación cliente proporcionar métodos alternativos para leer los datos desde el archivo ejecutable de archivo cuando el archivo no son accesibles directamente a través de E/S de archivos estándar.  
  
 Para cargar un archivo .pdb sin validación, utilice la [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) método.  
  
 Para validar el archivo .pdb en criterios específicos, use el [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) método.  
  
 Para cargar un archivo .pdb directamente desde la memoria, utilice el [Loaddatafromistream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) método.  
  
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
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [Idialoadcallback](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [Loadandvalidatedatafrompdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)