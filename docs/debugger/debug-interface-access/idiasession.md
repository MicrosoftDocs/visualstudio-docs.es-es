---
title: "IDiaSession | Microsoft Docs"
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
  - "IDiaSession (interface)"
ms.assetid: 69dab9bf-2c68-4f70-9678-3b50fba3e6fa
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Proporciona un contexto de consulta para los símbolos de depuración.  
  
## Sintaxis  
  
```  
IDiaSession : IUnknown  
```  
  
## Métodos  
 La tabla siguiente se muestran los métodos de `IDiaSession`.  
  
|Método|Descripción|  
|------------|-----------------|  
|[IDiaSession::get\_loadAddress](../../debugger/debug-interface-access/idiasession-get-loadaddress.md)|Recupera la dirección de la carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos.  Es el mismo valor que se pasó al método de `put_loadAddress` .|  
|[IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md)|Establece la dirección de la carga del archivo ejecutable que corresponde a los símbolos en este almacén de símbolos. **Note:**  Es importante llamar a este método cuando se obtiene un objeto de `IDiaSession` y antes de que comience con el objeto.|  
|[IDiaSession::get\_globalScope](../../debugger/debug-interface-access/idiasession-get-globalscope.md)|Recupera una referencia al ámbito global.|  
|[IDiaSession::getEnumTables](../../debugger/debug-interface-access/idiasession-getenumtables.md)|Recupera un enumerador para todas las tablas contenidas en el almacén de símbolos.|  
|[IDiaSession::getSymbolsByAddr](../../debugger/debug-interface-access/idiasession-getsymbolsbyaddr.md)|Recupera un enumerador de todos los símbolos denominados en ubicaciones estáticas.|  
|[IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)|Recupera todos los elementos secundarios de un identificador primario especificado que coincidan con el nombre y el tipo de token.|  
|[IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)|Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección especificada.|  
|[IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)|Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección relativa virtual especificada \(RVA\).|  
|[IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)|Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección virtual especificada \(VA\).|  
|[IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)|Recupera el token que contiene un token especificado de los metadatos.|  
|[IDiaSession::symsAreEquiv](../../debugger/debug-interface-access/idiasession-symsareequiv.md)|Comprueba si dos símbolos son equivalentes.|  
|[IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)|Recupera un símbolo por su identificador único.|  
|[IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)|Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección virtual y un desplazamiento relativos especificados.|  
|[IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)|Recupera un símbolo especificado con el que contiene, o es el más próximo a, una dirección virtual y un desplazamiento especificados.|  
|[IDiaSession::findFile](../../debugger/debug-interface-access/idiasession-findfile.md)|Recupera un archivo de código fuente por el compilando y nombre.|  
|[IDiaSession::findFileById](../../debugger/debug-interface-access/idiasession-findfilebyid.md)|Recupera un archivo de código fuente por el identificador de archivo de código fuente.|  
|[IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md)|Números de línea de recupera dentro de un identificador especificado de compilación y de archivo de código fuente.|  
|[IDiaSession::findLinesByAddr](../../debugger/debug-interface-access/idiasession-findlinesbyaddr.md)|Recupera las líneas de un compilación especificado con una dirección especificada.|  
|[IDiaSession::findLinesByRVA](../../debugger/debug-interface-access/idiasession-findlinesbyrva.md)|Recupera las líneas de un compilación especificado con una dirección relativa virtual especificada.|  
|[IDiaSession::findLinesByVA](../../debugger/debug-interface-access/idiasession-findlinesbyva.md)|Detecta información de número de línea para las líneas incluidas en un intervalo de direcciones especificado.|  
|[IDiaSession::findLinesByLinenum](../../debugger/debug-interface-access/idiasession-findlinesbylinenum.md)|Recupera las líneas de un compilación especificado por el archivo de código fuente y el número de línea.|  
|[IDiaSession::findInjectedSource](../../debugger/debug-interface-access/idiasession-findinjectedsource.md)|Recupera un origen que ha colocado en el almacén de símbolos con los proveedores de atributo u otros componentes del proceso de compilación.|  
|[IDiaSession::getEnumDebugStreams](../../debugger/debug-interface-access/idiasession-getenumdebugstreams.md)|Recupera una orden de secuencias de datos de depuración.|  
|[IDiaSession::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasession-findinlineframesbyaddr.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección especificada.|  
|[IDiaSession::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyrva.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección relativa virtual especificada \(RVA\).|  
|[IDiaSession::findInlineFramesByVA](../../debugger/debug-interface-access/idiasession-findinlineframesbyva.md)|Recupera una enumeración que permite que un cliente recorrer en iteración todos los marcos de punto flotante en una dirección virtual especificada \(VA\).|  
|[IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, el token primario especificado.|  
|[IDiaSession::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasession-findinlineelinesbyaddr.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, el token primario especificado y se contienen dentro del intervalo de direcciones especificado.|  
|[IDiaSession::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyrva.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, el token primario especificado y se contienen dentro de la dirección virtual relativa especificada \(RVA\).|  
|[IDiaSession::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasession-findinlineelinesbyva.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, el token primario especificado y se contienen dentro de la dirección virtual especificada \(VA\).|  
|[IDiaSession::findInlineeLinesByLinenum](../../debugger/debug-interface-access/idiasession-findinlineelinesbylinenum.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones que inline, directa o indirectamente, del archivo de código fuente y el número de línea especificados.|  
|[IDiaSession::findInlineesByName](../../debugger/debug-interface-access/idiasession-findinlineesbyname.md)|Recupera una enumeración que permite que un cliente recorra la información de número de línea de todas las funciones inline que coinciden con el nombre especificado.|  
|[IDiaSession::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsforacceleratorpointertag.md)|Devuelve una enumeración de los símbolos de la variable que el valor de etiqueta especificado corresponde a la función principal del código auxiliar de aceleradores.|  
|[IDiaSession::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasession-findsymbolsbyrvaforacceleratorpointertag.md)|Dado un valor de etiqueta correspondiente, este método devuelve una enumeración de los símbolos que se contienen en una función principal especificada de código auxiliar de aceleradores en una dirección relativa virtual especificada.|  
|[IDiaSession::findAcceleratorInlineesByName](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbyname.md)|Devuelve una enumeración de los símbolos para los marcos flotantes correspondiente al nombre especificado de la función inline.|  
|[IDiaSession::findAcceleratorInlineesByLinenum](../../debugger/debug-interface-access/idiasession-findacceleratorinlineesbylinenum.md)|Devuelve una enumeración de los símbolos para los marcos de punto flotante que corresponden a la ubicación especificada del origen.|  
  
## Comentarios  
 Es importante llamar al método de [IDiaSession::put\_loadAddress](../../debugger/debug-interface-access/idiasession-put-loadaddress.md) después de crear el objeto de `IDiaSession` \)y el valor pasado al método de `put_loadAddress` debe ser distinto de cero — para cualquier propiedad de \(VA\) de la dirección virtual de símbolos que estén accesibles.  La dirección de la carga procede de cualquier programa carga la aplicación ejecutable que se depure.  Por ejemplo, puede llamar a la función `GetModuleInformation` de Win32 para recuperar la dirección de la carga para la aplicación ejecutable, proporcionando un identificador al ejecutable.  
  
## Ejemplo  
 Este ejemplo muestra cómo obtener la interfaz de `IDiaSession` como parte de una inicialización general del diámetro SDK.  
  
```cpp#  
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
  
## Requisitos  
 Encabezado: Dia2.h  
  
 Biblioteca: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vea también  
 [Interfaces \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [Información general](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)   
 [Exe](../../debugger/debug-interface-access/exe.md)   
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)   
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)   
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)   
 [Consultar el archivo .pdb](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)