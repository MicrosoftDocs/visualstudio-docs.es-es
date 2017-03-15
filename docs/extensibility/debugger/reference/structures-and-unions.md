---
title: "Estructuras y uniones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "estructuras [Visual Studio SDK]"
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 11
---
# Estructuras y uniones
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Los siguientes son estructuras y uniones en Visual Studio de depuración SDK.  
  
 [AD\_PROCESS\_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Especifica el identificador de proceso, que puede ser un identificador de sistema o GUID.  
  
 [BP\_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Describe las condiciones en las que un punto de interrupción desencadenará.  
  
 [BP\_ERROR\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Describe la resolución de un punto de interrupción del error, incluyendo la ubicación, el programa, y subproceso.  
  
 [BP\_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Especifica el tipo de estructura utilizado para describir la ubicación del punto de interrupción.  
  
 [BP\_LOCATION\_CODE\_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Define los componentes que describen la ubicación de un punto de interrupción en una dirección en código.  
  
 [BP\_LOCATION\_CODE\_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Describe la ubicación de un punto de interrupción que se enlaza directamente a una dirección en el programa que se depura.  
  
 [BP\_LOCATION\_CODE\_FILE\_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 describe la ubicación de un punto de interrupción en la línea en un archivo de origen de código.  
  
 [BP\_LOCATION\_CODE\_FUNC\_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Describe la ubicación de desplazamiento de un punto de interrupción en una función en código.  
  
 [BP\_LOCATION\_CODE\_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Se utiliza para establecer los puntos de interrupción del código basándose en una cadena que el usuario puede escribir del IDE.  
  
 [BP\_LOCATION\_DATA\_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Se utiliza para establecer los puntos de interrupción de datos basados en una cadena que el usuario puede especificar del IDE.  
  
 [BP\_LOCATION\_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Describe la resolución de un punto de interrupción en una ubicación concreta.  
  
 [BP\_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Describe el recuento y condiciones sobre los que un punto de interrupción se después previamente el pasar desencadenado.  
  
 [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Contiene la información necesaria para implementar un punto de interrupción.  
  
 [BP\_REQUEST\_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Contiene la información necesaria para implementar un punto de interrupción \(igual que la estructura de [BP\_REQUEST\_INFO](../../../extensibility/debugger/reference/bp-request-info.md) pero incluye información de proveedor GUID, de la restricción y de seguimiento\).  
  
 [BP\_RESOLUTION\_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Describe la ubicación de un punto de interrupción del código.  
  
 [BP\_RESOLUTION\_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Describe el resultado de enlazar un punto de interrupción de datos.  
  
 [BP\_RESOLUTION\_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Describe la información enlazada de punto de interrupción para un punto de interrupción de código o un punto de interrupción de datos.  
  
 [BP\_RESOLUTION\_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Especifica la estructura de la ubicación de la resolución de punto de interrupción.  
  
 [BSTR\_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Describe una matriz de cadenas.  
  
 [BUILT\_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Especifica información sobre un tipo de campo tomado de metadatos.  
  
 [CODE\_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Describe una llamada a una función o método.  
  
 [COMPUTER\_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Describe el equipo en el que el depurador se está ejecutando.  
  
 [CONST\_GUID\_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Describe una lista de GUID.  
  
 [CONTEXT\_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Describe un contexto de memoria o contexto de código.  
  
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Describe una dirección en un programa que se depura.  
  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Representa uno de varios tipos diferentes de direcciones.  
  
 [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Identifica un visualizador personalizado de visor o tipo.  
  
 [DEBUG\_PROPERTY\_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Describe una propiedad de depuración que a su vez describe un objeto de naturaleza jerárquica con nombre, el tipo, y valor.  
  
 [DEBUG\_REFERENCE\_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 describe una referencia.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Describe el desensamblado al IDE para la presentación.  
  
 [EXCEPTION\_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Describe una excepción o un error en tiempo de ejecución produce el programa que se depura.  
  
 [FIELD\_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Describe la variable local, el parámetro, u otro campo.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 describe un marco de pila.  
  
 [GUID\_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Describe una matriz de identificadores únicos para los motores disponibles de depuración.  
  
 [JMC\_CODE\_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Se utiliza para establecer la información de JustMyCode para un módulo.  
  
 [MACHINE\_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 describe un equipo determinado.  
  
 [METADATA\_ADDRESS\_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Describe un elemento de matriz dentro de una matriz.  
  
 [METADATA\_ADDRESS\_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Describe la dirección de un campo de una clase o estructura.  
  
 [METADATA\_ADDRESS\_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Describe la dirección de una variable local dentro de un ámbito \(normalmente una función o un método\).  
  
 [METADATA\_ADDRESS\_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Describe la dirección de un método de una clase.  
  
 [METADATA\_ADDRESS\_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Describe un parámetro de un método o función.  
  
 [METADATA\_ADDRESS\_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Describe un valor devuelto de un método o función.  
  
 [METADATA\_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 describe un tipo de campo tomado de metadatos.  
  
 [MODULE\_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Describe un módulo set \(DLL, EXE, o ensamblado\).  
  
 [MODULE\_SYMBOL\_SEARCH\_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Describe la información de estado sobre las rutas de búsqueda de símbolos se han buscado que.  
  
 [NATIVE\_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Describe una dirección nativa.  
  
 [PDB\_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Describe un tipo de campo tomado de un símbolo PDB.  
  
 [PENDING\_BP\_STATE\_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Describe el estado de un punto de interrupción que esté listo para enlazar a una ubicación del código.  
  
 [PROCESS\_INFO](../../../extensibility/debugger/reference/process-info.md)  
 describe un proceso.  
  
 [PROGRAM\_NODE\_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Describe una lista de objetos de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) que representan nodos de programa.  
  
 [PROVIDER\_PROCESS\_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 describe los procesos que se ejecutan en un equipo.  
  
 [TEXT\_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Describe la ubicación de línea y columna del texto especificado.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 describe las propiedades de un subproceso.  
  
 [TYPE\_INFO](../../../extensibility/debugger/reference/type-info.md)  
 describe un tipo de campo.  
  
 [UNMANAGED\_ADDRESS\_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Describe una dirección física.  
  
 [UNMANAGED\_ADDRESS\_THIS\_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Describe una dirección relativa a un puntero de `this` \(`Me` en Visual Basic\).  
  
## Requisitos  
 encabezado: msdbg.h, sh.h, o ee.h  
  
 espacio de nombres: Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)