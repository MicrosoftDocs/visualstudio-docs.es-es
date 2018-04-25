---
title: IDiaSession | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession interface
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 7b2791f318a921a25535d5e9a8f17e2c595f1f56
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="idiasession"></a>IDiaSession
Proporciona un contexto de la consulta para los símbolos de depuración.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
IDiaSession : IUnknown  
```  
  
## <a name="methods"></a>Métodos  
 La tabla siguiente muestran los métodos de `IDiaSession`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaSession::get_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera la dirección de carga del archivo ejecutable que se corresponde con los símbolos de este almacén de símbolos. Este es el mismo valor que se pasó a la `put_loadAddress` método.|  
|[IDiaSession::put_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Establece la dirección de carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos. **Nota:** es importante llamar a este método cuando obtenga un `IDiaSession` de objetos y antes de empezar a usar el objeto.|  
|[IDiaSession::get_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera una referencia al ámbito global.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumerador para todas las tablas incluidas en el almacén de símbolos.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumerador para todos los símbolos con nombre en ubicaciones estáticos.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera a todos los elementos secundarios de un identificador de elemento primario especificado que coinciden con el tipo de nombre y el símbolo.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un tipo de símbolo especificado que contiene, o más cercana a una dirección especificada.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un tipo de símbolo especificado que contiene, o que esté más cercano a una dirección virtual relativa (RVA) especificada.|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un tipo de símbolo especificado que contiene, o que esté más cercano a una dirección virtual especificada (VA).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera el símbolo que contiene un token de metadatos especificado.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Comprueba si dos símbolos son equivalentes.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un símbolo de por su identificador único.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un tipo de símbolo especificado que contiene, o que esté más cercano a una dirección virtual relativa especificada y el desplazamiento.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un tipo de símbolo especificado que contiene, o que esté más cercano a una dirección virtual especificada y el desplazamiento.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un archivo de origen por operación de compilación y el nombre.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un archivo de código fuente mediante el identificador del archivo de origen.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Recupera los números de línea en un identificador de archivo de operación de compilación y el origen especificado.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera las líneas en una operación de compilación especificado que contienen una dirección especificada.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera las líneas en una operación de compilación especificado que contienen una dirección virtual relativa especificada.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Busca la información del número de línea para las líneas contenidas en un intervalo de direcciones especificado.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera las líneas de una operación de compilación especificado por el número de archivo y la línea de código fuente.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un origen que se ha colocado en el almacén de símbolos por los proveedores de atributo u otros componentes del proceso de compilación.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una secuencia enumerada de flujos de datos de depuración.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los fotogramas en línea en una dirección determinada.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los fotogramas en línea en una dirección virtual relativa (RVA) especificado.|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración todos los fotogramas en línea en una dirección virtual especificado (VA).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro del intervalo de direcciones especificado.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro de la dirección virtual relativa (RVA) especificada.|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones que se alinean, directamente o indirectamente, mediante el símbolo de elemento primario especificado y está dentro de la dirección virtual especificada (VA).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones que están entre líneas, directa o indirectamente, en el número de archivo y la línea de origen especificado.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera una enumeración que permite a un cliente recorrer en iteración la información del número de línea de todas las funciones insertadas que coinciden con un nombre especificado.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Devuelve una enumeración de símbolos para la variable que el valor de etiqueta especificado corresponde de la principal función de código auxiliar de acelerador.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de símbolos que se encuentran en una función de código auxiliar de acelerador primario especificado en una dirección virtual relativa especificada.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Devuelve una enumeración de símbolos para marcos flotantes correspondiente al nombre de función especificado en línea.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Devuelve una enumeración de símbolos para marcos flotantes que corresponden a la ubicación de origen especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Es importante llamar a la [idiasession:: Put_loadaddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) método después de crear el `IDiaSession` objeto y el valor pasado a la `put_loadAddress` método debe ser distinto de cero, para cualquier propiedad de dirección virtual (VA) de símbolos se puede obtener acceso. La dirección de carga procede de cualquier programa carga el archivo ejecutable que se está depurando. Por ejemplo, puede llamar a la función de Win32 `GetModuleInformation` para recuperar la dirección de carga para el ejecutable, especifica un identificador para el archivo ejecutable.  
  
## <a name="example"></a>Ejemplo  
 Este ejemplo muestra cómo obtener el `IDiaSession` interfaz como parte de una inicialización general del SDK de DIA.  
  
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
 [Idiadatasource:: OpenSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [Idiasymbol:: Findchildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)