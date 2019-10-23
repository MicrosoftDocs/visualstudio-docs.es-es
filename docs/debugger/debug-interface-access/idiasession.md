---
title: IDiaSession | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f983275974ed0ec3fb0e6091f5b9e73cdccd76ef
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72741854"
---
# <a name="idiasession"></a>IDiaSession
Proporciona un contexto de consulta para los símbolos de depuración.

## <a name="syntax"></a>Sintaxis

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Métodos
En la tabla siguiente se muestran los métodos de `IDiaSession`.

|Método|Descripción|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera la dirección de carga del archivo ejecutable que corresponde a los símbolos de este almacén de símbolos. Es el mismo valor que se pasó al método `put_loadAddress`.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos de este almacén de símbolos. **Nota:**  Es importante llamar a este método cuando se obtiene un objeto `IDiaSession` y antes de empezar a usar el objeto.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera una referencia al ámbito global.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumerador para todas las tablas contenidas en el almacén de símbolos.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumerador para todos los símbolos con nombre en ubicaciones estáticas.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera todos los elementos secundarios de un identificador primario especificado que coinciden con el nombre y el tipo de símbolo.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo de símbolo especificado que contiene o está más cerca de una dirección especificada.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo de símbolo especificado que contiene o está más cerca de una dirección virtual relativa (RVA) especificada.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo de símbolo especificado que contiene o está más cerca de una dirección virtual (VA) especificada.|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera el símbolo que contiene un token de metadatos especificado.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Comprueba si dos símbolos son equivalentes.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un símbolo por su identificador único.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo de símbolo especificado que contiene o está más cerca de una dirección virtual relativa y un desplazamiento especificados.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo de símbolo especificado que contiene o está más cerca de una dirección virtual y un desplazamiento especificados.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un archivo de código fuente mediante la operación de compilación y nombre.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un archivo de origen por el identificador del archivo de código fuente.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera los números de línea dentro de un identificador de archivo de código fuente y de compilación especificados.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera las líneas de una operación de compilación especificada que contienen una dirección especificada.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera las líneas de una operación de compilación especificada que contienen una dirección virtual relativa especificada.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Busca la información del número de línea para las líneas contenidas en un intervalo de direcciones especificado.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera las líneas de una operación de compilación especificada por el archivo de código fuente y el número de línea.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un origen que se ha colocado en el almacén de símbolos por proveedores de atributos u otros componentes del proceso de compilación.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una secuencia enumerada de flujos de datos de depuración.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los marcos insertados en una dirección determinada.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los marcos insertados en una dirección virtual relativa (RVA) especificada.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los marcos insertados en una dirección virtual especificada (VA).|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, por el símbolo primario especificado.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, por el símbolo primario especificado y que se encuentran dentro del intervalo de direcciones especificado.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, por el símbolo primario especificado y que están contenidas en la dirección virtual relativa (RVA) especificada.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, por el símbolo primario especificado y que se encuentran dentro de la dirección virtual especificada (VA).|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas, directa o indirectamente, en el archivo de código fuente y el número de línea especificados.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas que coinciden con un nombre especificado.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Devuelve una enumeración de símbolos para la variable a la que corresponde el valor de etiqueta especificado en la función de código auxiliar del acelerador primario.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de símbolos contenidos en una función de código auxiliar de acelerador primaria especificada en una dirección virtual relativa especificada.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Devuelve una enumeración de símbolos para los marcos insertados correspondientes al nombre de función insertada especificado.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Devuelve una enumeración de símbolos para los marcos insertados que corresponden a la ubicación de origen especificada.|

## <a name="remarks"></a>Comentarios
Es importante llamar al método [IDiaSession::P ut_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) después de crear el objeto `IDiaSession`, y el valor pasado al método `put_loadAddress` debe ser distinto de cero, para que se pueda tener acceso a las propiedades de cualquier dirección virtual (va) de los símbolos. La dirección de carga procede de cualquier programa cargado el ejecutable que se está depurando. Por ejemplo, puede llamar a la función de Win32 `GetModuleInformation` para recuperar la dirección de carga del archivo ejecutable, dado un identificador para el ejecutable.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo obtener la interfaz `IDiaSession` como parte de una inicialización general del SDK de DIA.

```C++
CComPtr<IDiaDataSource> pSource;
ComPtr<IDiaSession> psession;

void InitializeDIA(const char *szFilename)
{
    HRESULT hr = CoCreateInstance( CLSID_DiaSource,
                                   NULL,
                                   CLSCTX_INPROC_SERVER,
                                   __uuidof( IDiaDataSource ),
                                  (void **) &pSource);
    if (FAILED(hr))
    {
        Fatal("Could not CoCreate CLSID_DiaSource. Register msdia80.dll." );
    }
    wchar_t wszFilename[ _MAX_PATH ];
    mbstowcs( wszFilename,
              szFilename,
              sizeof( wszFilename )/sizeof( wszFilename[0] ) );
    if ( FAILED( pSource->loadDataFromPdb( wszFilename ) ) )
    {
        if ( FAILED( pSource->loadDataForExe( wszFilename, NULL, NULL ) ) )
        {
            Fatal( "loadDataFromPdb/Exe" );
        }
    }
    if ( FAILED( pSource->openSession( &psession ) ) )
    {
        Fatal( "openSession" );
    }
}
```

## <a name="requirements"></a>Requisitos
Encabezado: Dia2. h

Biblioteca: diaguids. lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
- [Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)
- [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)
- [Exe](../../debugger/debug-interface-access/exe.md)
- [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)
- [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)
- [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)
- [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)
- [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
