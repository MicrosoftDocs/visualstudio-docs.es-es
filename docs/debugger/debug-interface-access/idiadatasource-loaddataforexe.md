---
title: "IDiaDataSource::loadDataForExe | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource::loadDataForExe (método)"
ms.assetid: d94a1068-f53f-44b5-b6fb-00dec361a7f2
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# IDiaDataSource::loadDataForExe
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los Abrir y elabore los datos de depuración asociado al archivo de .exe\/.dll.  
  
## Sintaxis  
  
```cpp#  
HRESULT loadDataForExe (  
   LPCOLESTR executable,  
   LPCOLESTR searchPath,  
   IUnknown* pCallback  
);  
```  
  
#### Parámetros  
 ejecutable  
 \[in\]  Ruta de acceso al archivo .exe o .dll.  
  
 searchPath  
 \[in\]  Ruta de acceso alternativa a buscar los datos de depuración.  
  
 pCallback  
 \[in\]  Una interfaz de `IUnknown` para un objeto que admite una interfaz de devolución de llamada de depuración, como [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md), [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md), [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md), o las interfaces de [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) .  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  La tabla siguiente se muestran algunos de los códigos de error posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E\_PDB\_NOT\_FOUND|Error al abrir el archivo, o el archivo tiene un formato no válido.|  
|E\_PDB\_FORMAT|Ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E\_PDB\_INVALID\_SIG|la firma no coincide.|  
|E\_PDB\_INVALID\_AGE|la edad no coincide.|  
|E\_INVALIDARG|Parámetro no válido.|  
|E\_UNEXPECTED|el origen de datos se ha preparado ya.|  
  
## Comentarios  
 El encabezado de depuración de los nombres de archivo de .exe\/.dll la ubicación asociados de los datos de depuración.  
  
 Este método lee el encabezado y después las búsquedas de depuración para y prepara los datos de depuración.  El progreso de la búsqueda se puede, informes y controlar opcionalmente con devoluciones.  Por ejemplo, se invoca [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md) cuando el método de `IDiaDataSource::loadDataForExe` encuentra y procesa un directorio debug.  
  
 Las interfaces de [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md) y de [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md) permiten a la aplicación cliente para proporcionar métodos alternativos para leer datos del archivo ejecutable cuando el archivo no se puede tener acceso directamente a E\/S de archivo estándar.  
  
 Para cargar un archivo .pdb sin validación, use el método de [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) .  
  
 Para validar el archivo .pdb con los criterios específicos, utilice el método de [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Para cargar un archivo .pdb directamente de la memoria, utilice el método de [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## Ejemplo  
  
```cpp#  
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
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)   
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)   
 [IDiaLoadCallback::NotifyDebugDir](../../debugger/debug-interface-access/idialoadcallback-notifydebugdir.md)   
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)   
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)