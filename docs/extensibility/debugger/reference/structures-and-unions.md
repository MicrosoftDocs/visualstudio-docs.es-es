---
title: Estructuras y uniones | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 2da39e0327f9a0be2cf0f61227de5ea51af03285
ms.sourcegitcommit: 40d612240dc5bea418cd27fdacdf85ea177e2df3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/29/2019
ms.locfileid: "66329115"
---
# <a name="structures-and-unions"></a>Estructuras y uniones
Los siguientes son estructuras y uniones en el SDK de depuración de Visual Studio.

- [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md) especifica el identificador de proceso, que puede ser un identificador de sistema o un GUID.

- [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md) se describen las condiciones en las que se desencadenará un punto de interrupción.

- [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md) describe la resolución de un punto de interrupción de error, incluida la ubicación, el programa y subproceso.

- [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md) especifica el tipo de estructura que se utiliza para describir la ubicación del punto de interrupción.

- [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md) define los componentes que describen la ubicación de un punto de interrupción en una dirección en el código.

- [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md) describe la ubicación de un punto de interrupción que se enlaza directamente a una dirección en el programa que se está depurando.

- [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md) describe la ubicación de un punto de interrupción en la línea de un archivo de código fuente.

- [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md) describe la ubicación de desplazamiento de un punto de interrupción en una función en código.

- [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md) usa para establecer puntos de interrupción de código basados en una cadena que el usuario puede escribir desde el IDE.

- [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md) usa para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede escribir desde el IDE.

- [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md) describe la resolución de un punto de interrupción en una ubicación específica.

- [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md) describe el número y las condiciones en la que se desencadenará un punto de interrupción después de tener previamente se ha pasado.

- [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) contiene la información necesaria para implementar un punto de interrupción.

- [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md) contiene la información necesaria para implementar un punto de interrupción (igual que el [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estructura, pero incluye información de GUID, la restricción y punto de seguimiento del proveedor).

- [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md) describe la ubicación de un punto de interrupción del código.

- [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md) describe el resultado de un punto de interrupción de datos de enlace.

- [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md) se describe la información de punto de interrupción enlazado para un punto de interrupción de código o un punto de interrupción de datos.

- [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md) especifica la estructura de la ubicación de la resolución de punto de interrupción.

- [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md) describe una matriz de cadenas.

- [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md) especifica información sobre un tipo de campo que se toman de los metadatos.

- [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) describe una llamada a una función o método.

- [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md) describe el equipo donde se ejecuta el depurador.

- [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md) describe una lista de GUID.

- [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md) describe un contexto de la memoria o el contexto del código.

- [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) describe una dirección en un programa que se está depurando.

- [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md) representa uno de los diferentes tipos de direcciones.

- [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) identifica un visor personalizado o visualizador de tipo.

- [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) describe una propiedad de depuración que a su vez describe un objeto de una naturaleza jerárquica que tiene el nombre, tipo y valor.

- [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) describe una referencia.

- [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md) describe desensamblado en el IDE para su presentación.

- [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md) describe un error de tiempo de ejecución o de excepción producido por el programa que se está depurando.

- [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md) describe otro campo, parámetro o una variable local.

- [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) describe un marco de pila.

- [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md) describe una matriz de identificadores únicos para los motores de depuración disponible.

- [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md) usa para establecer la información de JustMyCode de un módulo.

- [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md) describe un equipo determinado.

- [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md) describe un elemento de matriz dentro de una matriz.

- [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md) describe la dirección de un campo de una clase o estructura.

- [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md) describe la dirección de una variable local dentro de un ámbito (normalmente una función o método).

- [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md) describe la dirección de un método de una clase.

- [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md) describe un parámetro de un método o función.

- [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md) describe un valor devuelto de un método o función.

- [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md) describe un tipo de campo que se toman de los metadatos.

- [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md) describe un módulo determinado (ensamblado, EXE o DLL).

- [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md) describe la información de estado sobre las rutas de acceso de búsqueda de símbolos que se ha buscado.

- [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md) describe una dirección nativa.

- [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md) describe un tipo de campo realizado desde un símbolo PDB.

- [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md) describe el estado de un punto de interrupción que está listo para enlazar a una ubicación del código.

- [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md) describe un proceso.

- [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md) describe una lista de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que representan nodos de programa.

- [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md) describe los procesos que se ejecutan en un equipo.

- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) describe la ubicación de línea y columna en el texto dado.

- [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md) se describen las propiedades de un subproceso.

- [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md) describe un tipo de campo.

- [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md) describe una dirección física.

- [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md) describe una dirección que es relativa a un `this` puntero (`Me` en Visual Basic).

## <a name="requirements"></a>Requisitos
 Encabezado: msdbg.h, sh.h o ee.h

 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop

 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Vea también
- [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)