---
title: "IDiaDataSource::loadDataFromPdb | Microsoft Docs"
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
  - "IDiaDataSource::loadDataFromPdb (método)"
ms.assetid: 02159073-8144-47f8-a0b0-aa0edcb92b5b
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# IDiaDataSource::loadDataFromPdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los Abrir y desarrollan un archivo de base de datos de programa \(.pdb\) como origen de datos de depuración.  
  
## Sintaxis  
  
```cpp#  
HRESULT loadDataFromPdb (  
   LPCOLESTR pdbPath  
);  
```  
  
#### Parámetros  
 pdbPath  
 \[in\]  La ruta de acceso al archivo .pdb.  
  
## Valor devuelto  
 Si finaliza correctamente, devuelve `S_OK`; de lo contrario, devuelve un código de error.  la tabla siguiente muestra los valores devueltos posibles para este método.  
  
|Valor|Descripción|  
|-----------|-----------------|  
|E\_PDB\_NOT\_FOUND|Error al abrir el archivo, o si se determina que el archivo tiene un formato no válido.|  
|E\_PDB\_FORMAT|Ha intentado obtener acceso a un archivo con un formato obsoleto.|  
|E\_INVALIDARG|Parámetro no válido.|  
|E\_UNEXPECTED|el origen de datos se ha preparado ya.|  
  
## Comentarios  
 Este método carga los datos de depuración directamente de un archivo .pdb.  
  
 Para validar el archivo .pdb con los criterios específicos, utilice el método de [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md) .  
  
 Para obtener acceso al proceso de carga de datos \(a través de un mecanismo de devolución de llamada\), utilice el método de [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) .  
  
 Para cargar un archivo .pdb directamente de la memoria, utilice el método de [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md) .  
  
## Ejemplo  
  
```cpp#  
HRESULT hr = pSource->loadDataFromPdb( L"myprog.pdb" );  
if (FAILED(hr))  
{  
    // report error  
}  
```  
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)   
 [IDiaDataSource::loadAndValidateDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loadandvalidatedatafrompdb.md)   
 [IDiaDataSource::loadDataFromIStream](../../debugger/debug-interface-access/idiadatasource-loaddatafromistream.md)