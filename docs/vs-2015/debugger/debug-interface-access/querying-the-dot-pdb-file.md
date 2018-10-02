---
title: Consultar el. Archivo PDB | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
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
- PDB files
- .pdb files, querying
ms.assetid: 8da07d1c-2712-45f9-8fbf-f34040408a8a
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: fae3034cf9f02d6d37c55bafe392610b1f1544fb
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47577566"
---
# <a name="querying-the-pdb-file"></a>Consultar el archivo .pdb
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [consulta el. Archivo PDB](https://docs.microsoft.com/visualstudio/debugger/debug-interface-access/querying-the-dot-pdb-file).  
  
Un archivo de base de datos de programa (extensión .pdb) es un archivo binario que contiene el tipo y la información de depuración simbólica recopilada durante el transcurso de compilar y vincular el proyecto. Se crea un archivo PDB cuando se compila un programa de C o C++ con **/Zi** o **/Zi** o un [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], [!INCLUDE[csprcs](../../includes/csprcs-md.md)], o [!INCLUDE[jsprjscript](../../includes/jsprjscript-md.md)] programar con el **/debug** opción. Los archivos objeto contienen referencias en el archivo .pdb de la información de depuración. Para obtener más información sobre los archivos pdb, consulte [archivos PDB](http://msdn.microsoft.com/en-us/1761c84e-8c2c-4632-9649-b5f99964ed3f). Una aplicación de DIA puede usar los siguientes pasos generales para obtener más detalles sobre los distintos símbolos, objetos y elementos de datos dentro de una imagen ejecutable.  
  
### <a name="to-query-the-pdb-file"></a>Para consultar el archivo .pdb  
  
1.  Adquirir un origen de datos mediante la creación de un [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md) interfaz.  
  
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
  
2.  Llame a [Loaddatafrompdb](../../debugger/debug-interface-access/idiadatasource-loaddatafrompdb.md) o [Loaddataforexe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) para cargar la información de depuración.  
  
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
  
3.  Llame a [Idiadatasource](../../debugger/debug-interface-access/idiadatasource-opensession.md) para abrir un [IDiaSession](../../debugger/debug-interface-access/idiasession.md) para obtener acceso a la información de depuración.  
  
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
  
5.  Use el `IDiaEnum*` interfaces para enumerar y examinar los símbolos u otros elementos de información de depuración.  
  
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
  
## <a name="see-also"></a>Vea también  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)



