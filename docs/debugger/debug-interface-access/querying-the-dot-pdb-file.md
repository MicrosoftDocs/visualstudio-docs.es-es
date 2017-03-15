---
title: "Consultar el archivo .pdb | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "PDB (archivos)"
  - "archivos .pdb, consultas"
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Consultar el archivo .pdb
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un archivo de base de datos de programa \(extensión .pdb\) es un archivo binario que contiene el tipo y la información de depuración simbólica recopilados a lo largo de edificio y vincular el proyecto.  Se crea un archivo PDB cuando se compila un programa escrito en C\/C\+\+. \/C \+\+ con **\/ZI** o **\/Zi** o [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o programa de [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] con la opción de **\/debug** .  Los archivos objeto contienen referencias en el archivo .pdb para la información de depuración.  Para obtener más información sobre los archivos de pdb, vea [PDB Files](http://msdn.microsoft.com/es-es/1761c84e-8c2c-4632-9649-b5f99964ed3f).  Una aplicación de diámetro puede utilizar los pasos generales siguientes para obtener detalles sobre los símbolos diferentes, objetos, y datos de una imagen ejecutable.  
  
### Para ver el archivo .pdb  
  
1.  adquiera un origen de datos creando una interfaz de [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) .  
  
    ```cpp#  
    CComPtr<IDiaDataSource> pSource;  
    hr = CoCreateInstance( CLSID_DiaSource,  
                           NULL,  
                           CLSCTX_INPROC_SERVER,  
                           __uuidof( IDiaDataSource ),  
                          (void **) &pSource);  
  
    if (FAILED(hr))  
    {  
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );  
    }  
    ```  
  
2.  Llame a [IDiaDataSource::loadDataFromPdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) o [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para cargar la información de depuración.  
  
    ```cpp#  
    wchar_t wszFilename[ _MAX_PATH ];  
    mbstowcs( wszFilename, szFilename, sizeof( wszFilename )/sizeof( wszFilename[0] ) );  
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )  
    {  
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )  
        {  
            Fatal( "loadDataFromPdb/Exe" );  
        }  
    }  
    ```  
  
3.  Llame a [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) para abrir [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para obtener acceso a información de depuración.  
  
    ```cpp#  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Use los métodos de `IDiaSession` para consultar los símbolos en el origen de datos.  
  
    ```cpp#  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Use las interfaces de `IDiaEnum*` para enumerar y buscar a través de los símbolos u otros elementos de información de depuración.  
  
    ```cpp#  
    CComPtr<IDiaEnumTables> pTables;  
    if ( FAILED( psession->getEnumTables( &pTables ) ) )  
    {  
        Fatal( "getEnumTables" );  
    }  
    CComPtr< IDiaTable > pTable;  
    while ( SUCCEEDED( hr = pTables->Next( 1, &pTable, &celt ) ) && celt == 1 )  
    {  
         // Do something with each IDiaTable.  
    }  
    ```  
  
## Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)