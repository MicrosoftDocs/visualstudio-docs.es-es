---
title: "Interfaces (Debug Interface Access SDK) | Microsoft Docs"
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
  - "interfaces [Kit de desarrollo DIA (SDK)]"
  - "Kit de desarrollo DIA (SDK), interfaces"
ms.assetid: 62aee7c3-d314-4272-a32b-b2818f32fab8
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Interfaces (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Los métodos se muestran alfabéticamente en cada interfaz en la tabla de contenido y en la interfaz en el orden de Vtable.  
  
## En esta sección  
 [IDiaAddressMap](../../debugger/debug-interface-access/idiaaddressmap.md)  
 Proporciona control sobre cómo el diámetro SDK calcula las direcciones virtuales y relativas para los objetos de depuración.  
  
 [IDiaDataSource](../../debugger/debug-interface-access/idiadatasource.md)  
 Inicia el acceso a un origen de símbolos de depuración.  
  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)  
 Proporciona acceso a los registros en una secuencia de datos de depuración.  
  
 [IDiaEnumDebugStreams](../../debugger/debug-interface-access/idiaenumdebugstreams.md)  
 Muestra las distintas secuencias de depuración contenidas en el origen de datos.  
  
 [IDiaEnumFrameData](../../debugger/debug-interface-access/idiaenumframedata.md)  
 Muestra los distintos datos de cuadro contenido en el origen de datos.  
  
 [IDiaEnumInjectedSources](../../debugger/debug-interface-access/idiaenuminjectedsources.md)  
 Enumere los diferentes orígenes insertados contenidos en el origen de datos.  
  
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)  
 Muestra los distintos números de línea contenido en el origen de datos.  
  
 [IDiaEnumSectionContribs](../../debugger/debug-interface-access/idiaenumsectioncontribs.md)  
 Muestra las distintas contribuciones de la sección contenidas en el origen de datos.  
  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)  
 Enumera los segmentos diferentes contenido en el origen de datos.  
  
 [IDiaEnumSourceFiles](../../debugger/debug-interface-access/idiaenumsourcefiles.md)  
 Muestra los distintos archivos de código fuente contenidos en el origen de datos.  
  
 [IDiaEnumStackFrames](../../debugger/debug-interface-access/idiaenumstackframes.md)  
 Muestra los distintos marcos de pila disponible.  
  
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)  
 Enumera los símbolos diferentes contenido en el origen de datos.  
  
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)  
 Enumera por la dirección que los símbolos diferentes contenían en el origen de datos.  
  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)  
 Muestra las distintas tablas contenidas en el origen de datos.  
  
 [IDiaFrameData](../../debugger/debug-interface-access/idiaframedata.md)  
 expone los detalles de un marco de pila.  
  
 [IDiaImageData](../../debugger/debug-interface-access/idiaimagedata.md)  
 Expone los detalles de las diferencias de la ubicación base y de memoria del módulo o de imagen.  
  
 [IDiaInjectedSource](../../debugger/debug-interface-access/idiainjectedsource.md)  
 Tiene acceso al código fuente del programa almacenado en el origen de datos del diámetro.  
  
 [IDiaLineNumber](../../debugger/debug-interface-access/idialinenumber.md)  
 Tiene acceso a la información que describe el proceso de asignación de un bloque de bytes de texto de la imagen a un número de línea del archivo de código fuente.  
  
 [IDiaLoadCallback](../../debugger/debug-interface-access/idialoadcallback.md)  
 Recibe devoluciones de llamada del símbolo de diámetro que encuentra procedimiento, para habilitar una interfaz de usuario para informar del progreso del intento de la ubicación.  
  
 [IDiaLoadCallback2](../../debugger/debug-interface-access/idialoadcallback2.md)  
 Recibe devoluciones de llamada del símbolo de diámetro que encuentra procedimiento, lo que las restricciones son impuesta sobre el proceso que localice.  
  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)  
 Permite leer las propiedades persistentes de un conjunto de propiedades del diámetro.  
  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)  
 Permite a una aplicación cliente para proporcionar bytes de un archivo ejecutable según lo especificado por la posición del archivo.  
  
 [IDiaReadExeAtOffsetCallback](../../debugger/debug-interface-access/idiareadexeatoffsetcallback.md)  
 Permite a una aplicación cliente para proporcionar bytes de un archivo ejecutable especificados por una dirección relativa virtual.  
  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)  
 Recupera los datos que describen una contribución de la sección, es decir, un bloque de memoria contiguo participado en la imagen por un compilando.  
  
 [IDiaSegment](../../debugger/debug-interface-access/idiasegment.md)  
 Datos de asignaciones de número de sección a los segmentos del espacio de direcciones.  
  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)  
 Proporciona un contexto de consulta para los símbolos de depuración.  
  
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)  
 representa un archivo de código fuente.  
  
 [IDiaStackFrame](../../debugger/debug-interface-access/idiastackframe.md)  
 expone las propiedades de un marco de pila.  
  
 [IDiaStackWalker](../../debugger/debug-interface-access/idiastackwalker.md)  
 Proporciona métodos para que un recorrido de pila utilizando el archivo PDB.  
  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)  
 Mantiene contexto de pila entre las invocaciones de método de [IDiaFrameData::execute](../../debugger/debug-interface-access/idiaframedata-execute.md) .  
  
 [IDiaStackWalkHelper](../../debugger/debug-interface-access/idiastackwalkhelper.md)  
 Facilitates que recorre la pila utilizando el archivo de base de datos de depuración de programa \(PDB\).  
  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)  
 Describe las propiedades de una instancia del símbolo.  
  
 [IDiaTable](../../debugger/debug-interface-access/idiatable.md)  
 Muestra una tabla de origen de datos del diámetro.  
  
## Secciones relacionadas  
 [Enumeraciones y estructuras](../../debugger/debug-interface-access/enumerations-and-structures.md)  
 Describe las enumeraciones y estructuras utilizadas por distintas interfaces de diámetro SDK.  
  
 [Constantes \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/constants-debug-interface-access-sdk.md)  
 Describe las constantes disponibles en el diámetro SDK.  
  
## Vea también  
 [Referencia](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)