---
title: Consultar el. Archivo PDB | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcc97fc6c508a47088cb2e96c9132c88c8fcb75c
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "54996819"
---
# <a name="querying-the-pdb-file"></a>Consultar el archivo .pdb
Un archivo de base de datos de programa (extensión .pdb) es un archivo binario que contiene el tipo y la información de depuración simbólica recopilada durante el transcurso de compilar y vincular el proyecto. Se crea un archivo PDB cuando se compila un programa de C o C++ con **/Zi** o **/Zi** o un [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)], o [!INCLUDE[jsprjscript](../../debugger/debug-interface-access/includes/jsprjscript_md.md)] programar con el **/debug** opción. Los archivos objeto contienen referencias en el archivo .pdb de la información de depuración. Para obtener más información sobre los archivos pdb, consulte [archivos PDB](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/yd4f8bd1(v=vs.100)). Una aplicación de DIA puede usar los siguientes pasos generales para obtener más detalles sobre los distintos símbolos, objetos y elementos de datos dentro de una imagen ejecutable.  
  
### <a name="to-query-the-pdb-file"></a>Para consultar el archivo .pdb  
  
1.  Adquirir un origen de datos mediante la creación de un [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interfaz.  
  
    ```C++  
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
  
2.  Llame a [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) o [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para cargar la información de depuración.  
  
    ```C++  
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
  
3.  Llame a [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) para abrir un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para obtener acceso a la información de depuración.  
  
    ```C++  
    CComPtr<IDiaSession> psession;  
    if ( FAILED( pSource->openSession( &psession ) ) )   
    {  
        Fatal( "openSession" );  
    }  
    ```  
  
4.  Use los métodos de `IDiaSession` para consultar los símbolos en el origen de datos.  
  
    ```C++  
    CComPtr<IDiaSymbol> pglobal;  
    if ( FAILED( psession->get_globalScope( &pglobal) ) )  
    {  
        Fatal( "get_globalScope" );  
    }  
    ```  
  
5.  Use el `IDiaEnum*` interfaces para enumerar y examinar los símbolos u otros elementos de información de depuración.  
  
    ```C++  
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
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)