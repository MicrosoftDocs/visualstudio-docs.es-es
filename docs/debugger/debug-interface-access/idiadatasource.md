---
title: "IDiaDataSource | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaDataSource (interfaz)"
ms.assetid: 6260ac76-4f9d-4144-ba22-32f8620b32c2
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaDataSource
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Inicia el acceso a un origen de símbolos de depuración.  
  
## Sintaxis  
  
```  
IDiaDataSource : IUnknown  
```  
  
## métodos en el orden de Vtable  
 La tabla siguiente se muestran los métodos de `IDiaDataSource`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaDataSource::get\_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md)|recupera el nombre de archivo para el error de carga pasado.|  
|[IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md)|Los Abrir y desarrollan un archivo de base de datos de programa \(.pdb\) como origen de datos de depuración.|  
|[IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)|Abra y compruebe que coincida con el archivo de base de datos de programa \(.pdb\) la información de firma proporcionada; prepara el archivo .pdb como origen de datos de depuración.|  
|[IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)|Los Abrir y elabore los datos de depuración asociado al archivo de .exe\/.dll.|  
|[IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)|Prepara los datos de depuración almacenados en un archivo de base de datos de programa \(.pdb\) tiene acceso mediante un flujo de datos en memoria.|  
|[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)|Abra una sesión para ver símbolos.|  
  
## Comentarios  
 Una llamada a uno de los métodos de carga de la interfaz de `IDiaDataSource` abra el origen del token.  Una llamada correcta al método de [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) devuelve una interfaz de [IDiaSession](../../debugger/debug-interface-access/idiasession.md) que admita consultar el origen de datos.  Si el método load devuelve un error archivo\-relacionado el valor devuelto del método de [IDiaDataSource::get\_lastError](../../debugger/debug-interface-access/idiadatasource-get-lasterror.md) contiene el nombre de archivo asociada al error.  
  
## Notas para los llamadores  
 Esta interfaz se obtiene llamando a la función de `CoCreateInstance` con el identificador de clase `CLSID_DiaSource` y el identificador de la interfaz de `IID_IDiaDataSource`.  el ejemplo muestra cómo se obtiene esta interfaz.  
  
## Ejemplo  
  
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
  
## Requisitos  
 encabezado: Dia2.h  
  
 biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)