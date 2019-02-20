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
ms.openlocfilehash: 26293210bfc0dc18ded747ef44c5cc8699b3c5c8
ms.sourcegitcommit: 22b73c601f88c5c236fe81be7ba4f7f562406d75
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 02/13/2019
ms.locfileid: "56227779"
---
# <a name="idiasession"></a>IDiaSession
Proporciona un contexto de consulta para símbolos de depuración.

## <a name="syntax"></a>Sintaxis

```
IDiaSession : IUnknown
```

## <a name="methods"></a>Métodos
La tabla siguiente muestran los métodos de `IDiaSession`.

|Método|Descripción|
|------------|-----------------|
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera la dirección de carga del archivo ejecutable que se corresponde con los símbolos de este almacén de símbolos. Este es el mismo valor que se pasó a la `put_loadAddress` método.|
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos. **Nota:** es importante llamar a este método cuando reciba un `IDiaSession` de objetos y antes de empezar a usar el objeto.|
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera una referencia al ámbito global.|
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumerador para todas las tablas contenidas en el almacén de símbolos.|
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumerador para todos los símbolos con nombre en ubicaciones estáticos.|
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera a todos los elementos secundarios de un identificador de elemento primario especificado que coinciden con el tipo de nombre y el símbolo.|
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección especificada.|
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección virtual relativa (RVA) especificada.|
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección virtual especificada (VA).|
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera el símbolo que contiene un token de metadatos especificado.|
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Comprueba si dos símbolos son equivalentes.|
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un símbolo por su identificador único.|
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección virtual relativa especificada y el desplazamiento.|
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección virtual especificada y el desplazamiento.|
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un archivo de código fuente mediante la operación de compilación y el nombre.|
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un archivo de código fuente por identificador de archivo de origen.|
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera los números de línea dentro de un identificador de archivo de origen y la operación de compilación especificado.|
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera las líneas en una operación de compilación especificado que contienen una dirección especificada.|
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera las líneas en una operación de compilación especificado que contienen una dirección virtual relativa especificada.|
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Busca la información de número de línea para las líneas contenidas en un intervalo de direcciones especificado.|
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera las líneas en una operación de compilación especificada por el número de archivo y la línea de origen.|
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un origen que se ha insertado en el almacén de símbolos por los proveedores de atributos u otros componentes del proceso de compilación.|
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una secuencia enumerada de flujos de datos de depuración.|
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos en línea en una dirección determinada.|
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos en línea en una dirección virtual relativa (RVA) especificado.|
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos en línea en una dirección virtual especificado (VA).|
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado.|
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro del intervalo de direcciones especificado.|
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro de la dirección virtual relativa (RVA) especificada.|
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro de la dirección virtual especificada (VA).|
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones que están insertadas, directa o indirectamente, en el número de archivo y la línea de origen especificado.|
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera una enumeración que permite que un cliente iterar por la información de número de línea de todas las funciones insertadas que coinciden con un nombre especificado.|
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Devuelve una enumeración de símbolos de la variable que el valor de etiqueta especificado corresponde de la principal función de código auxiliar del acelerador.|
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dado un valor de la etiqueta correspondiente, este método devuelve una enumeración de los símbolos que se encuentran en una función de código auxiliar del Acelerador primario especificado en una dirección virtual relativa especificada.|
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Devuelve una enumeración de los símbolos para los marcos en línea que corresponde al nombre de función en línea especificada.|
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Devuelve una enumeración de los símbolos para los marcos flotantes que corresponden a la ubicación de origen especificado.|

## <a name="remarks"></a>Comentarios
Es importante llamar a la [Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) método después de crear el `IDiaSession` objeto y el valor pasado a la `put_loadAddress` método debe ser distinto de cero, para cualquier propiedad de dirección virtual (VA) de los símbolos se puede obtener acceso. La dirección de carga procede de la carga de cualquier programa ejecutable que se está depurando. Por ejemplo, puede llamar a la función de Win32 `GetModuleInformation` para recuperar la dirección de carga para el ejecutable, dado un identificador al archivo ejecutable.

## <a name="example"></a>Ejemplo
En este ejemplo se muestra cómo obtener el `IDiaSession` interfaz como parte de una inicialización general de DIA (SDK).

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
Encabezado: Dia2.h

Biblioteca: diaguids.lib

DLL: msdia80.dll

## <a name="see-also"></a>Vea también
[Interfaces (Debug Interface Access SDK)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)  
[Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
[Exe](../../debugger/debug-interface-access/exe.md)  
[IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
[IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
[IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)  
[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)  
[Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)
