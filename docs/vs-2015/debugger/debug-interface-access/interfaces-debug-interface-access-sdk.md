---
title: Interfaces (Debug Interface Access SDK) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 5eaf63ac57610e9ebde6703f0b5c15bf9607fdde
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150873"
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfaces (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Los métodos se muestran en orden alfabético en cada interfaz de la tabla de contenido y en la página de la interfaz en orden vtable.  
  
## <a name="in-this-section"></a>En esta sección  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Proporciona control sobre cómo el SDK de DIA calcula las direcciones virtuales virtuales y relativas para los objetos de depuración.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Inicia el acceso a un origen de símbolos de depuración.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Proporciona acceso a los registros de un flujo de datos de depuración.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Enumera las diversas secuencias de depuración contenidas en el origen de datos.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Enumera los distintos elementos de datos de marco incluidos en el origen de datos.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Enumerar los distintos orígenes insertados contenidos en el origen de datos.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Enumera los distintos números de línea contenidos en el origen de datos.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Enumera las distintas contribuciones de la sección contenida en el origen de datos.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Enumera los distintos segmentos incluidos en el origen de datos.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Enumera los distintos archivos de código fuente incluidos en el origen de datos.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Enumera los distintos marcos de pila disponibles.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Enumera los distintos símbolos incluidos en el origen de datos.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Enumera por dirección los distintos símbolos incluidos en el origen de datos.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Enumera las distintas tablas contenidas en el origen de datos.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Expone los detalles de un marco de pila.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Expone los detalles de la ubicación base y los desplazamientos de memoria del módulo o de la imagen.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Obtiene acceso al código fuente del programa almacenado en el origen de datos DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Obtiene acceso a información que describe el proceso de asignación de un bloque de bytes de texto de imagen a un número de línea del archivo de código fuente.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Recibe las devoluciones de llamada del procedimiento de búsqueda de símbolos de DIA, lo que permite a una interfaz de usuario informar sobre el progreso del intento de ubicación.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Recibe las devoluciones de llamada del procedimiento de búsqueda de símbolos de DIA, lo que permite imponer restricciones en el proceso de búsqueda.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Permite leer las propiedades persistentes de un conjunto de propiedades DIA.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Permite que una aplicación cliente suministre bytes de un archivo ejecutable según lo especificado por la posición del archivo.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Permite que una aplicación cliente suministre bytes de un archivo ejecutable según lo especificado por una dirección virtual relativa.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Recupera los datos que describen una contribución de sección, es decir, un bloque de memoria contiguo que ha contribuido a la imagen mediante una operación de compilación.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Asigna datos del número de sección a segmentos de espacio de direcciones.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Proporciona un contexto de consulta para los símbolos de depuración.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Representa un archivo de código fuente.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Expone las propiedades de un marco de pila.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Proporciona métodos para realizar un recorrido de pila mediante el archivo PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Mantiene el contexto de pila entre las invocaciones del método [IDiaFrameData:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Facilita el recorrido de la pila mediante el archivo de la base de datos de depuración del programa (PDB).  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Describe las propiedades de una instancia de símbolo.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Enumera una tabla de origen de datos DIA.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Describe las enumeraciones y estructuras usadas por las distintas interfaces del SDK de DIA.  
  
 [Constantes (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Describe las constantes disponibles en el SDK de DIA.  
  
## <a name="see-also"></a>Consulte también  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)
