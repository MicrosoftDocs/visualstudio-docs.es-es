---
title: Interfaces (Debug Interface Access SDK) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interfaces [DIA SDK]
- DIA SDK, interfaces
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: "16"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: e128aa0a4cbb30106981b152252ff308e21669b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="interfaces-debug-interface-access-sdk"></a>Interfaces (Debug Interface Access SDK)
Métodos aparecen por orden alfabético en cada interfaz en la tabla de contenido y en la página de interfaz en orden de Vtable.  
  
## <a name="in-this-section"></a>En esta sección  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Proporciona control sobre cómo el SDK de DIA calcula direcciones virtuales relativas y virtuales para los objetos de depuración.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Inicia el acceso a un origen de símbolos de depuración.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Proporciona acceso a los registros de un flujo de datos de depuración.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Enumera los distintos flujos de depuración contenidos en el origen de datos.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Enumera los distintos elementos de datos de marco contenidos en el origen de datos.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Enumerar los diversos orígenes insertados contenidos en el origen de datos.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Enumera los números de línea distintos contenidos en el origen de datos.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Enumera las distintas contribuciones de sección contenidas en el origen de datos.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Enumera los distintos segmentos incluidos en el origen de datos.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Enumera los diversos archivos de origen contenidos en el origen de datos.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Enumera los distintos marcos de pila disponible.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Enumera los símbolos distintos contenidos en el origen de datos.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Enumera por dirección los símbolos distintos contenidos en el origen de datos.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Enumera las distintas tablas contenidas en el origen de datos.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 Expone los detalles de un marco de pila.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Expone los detalles de los desplazamientos de memoria y la ubicación base del módulo o la imagen.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Accesos el código fuente del programa que se almacena en el origen de datos DIA.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Accede a información que describe el proceso de asignación de un bloque de bytes de texto de la imagen a un número de línea del archivo de código fuente.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Recibe las devoluciones de llamada desde el símbolo DIA localizar procedimiento, lo que permite una interfaz de usuario indicar el progreso del intento de ubicación.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Recibe las devoluciones de llamada desde el símbolo DIA localizar procedimiento, lo que permite las restricciones que se pueden imponer en el proceso de localización.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Permite leer las propiedades de un conjunto de propiedades DIA persistentes.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Habilita una aplicación cliente proporcionar los bytes de un archivo ejecutable como especificado por la posición del archivo.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Habilita una aplicación cliente proporcionar los bytes de un archivo ejecutable según lo especificado por una dirección virtual relativa.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Recupera los datos que describen una contribución de sección, es decir, un bloque de memoria contiguo han contribuido a la imagen por una operación de compilación.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Asigna datos desde el número de sección a segmentos del espacio de direcciones.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Proporciona un contexto de la consulta para los símbolos de depuración.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 Representa un archivo de origen.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 Expone las propiedades de un marco de pila.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Proporciona métodos para realizar una pila del recorrido con el archivo PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Mantiene el contexto de la pila entre las distintas invocaciones de la [idiaframedata:: Execute](../../debugger/debug-interface-access/idiaframedata-execute.md) método.  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Facilita el recorrido de la pila utilizando el archivo de base de datos (PDB) de depuración de programa.  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Describe las propiedades de una instancia de símbolo.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Enumera una tabla de origen de datos DIA.  
  
## <a name="related-sections"></a>Secciones relacionadas  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Describe las enumeraciones y estructuras utilizadas por las diversas interfaces del SDK de DIA.  
  
 [Constantes (Debug Interface Access SDK)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Describe las constantes disponibles en el SDK de DIA.  
  
## <a name="see-also"></a>Vea también  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)