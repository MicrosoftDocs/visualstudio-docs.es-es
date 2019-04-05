---
title: Estructuras y uniones | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
helpviewer_keywords:
- structures [Visual Studio SDK]
ms.assetid: 9ff0a8f8-1ee6-4fdd-8b80-206436ff589b
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f882eae12e700fe86ab747cc7ffbe3b5744298af
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/23/2019
ms.locfileid: "58987591"
---
# <a name="structures-and-unions"></a>Estructuras y uniones
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Los siguientes son estructuras y uniones en el SDK de depuración de Visual Studio.  
  
 [AD_PROCESS_ID](../../../extensibility/debugger/reference/ad-process-id.md)  
 Especifica el identificador de proceso, que puede ser un identificador de sistema o un GUID.  
  
 [BP_CONDITION](../../../extensibility/debugger/reference/bp-condition.md)  
 Describe las condiciones en las que se desencadenará un punto de interrupción.  
  
 [BP_ERROR_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-error-resolution-info.md)  
 Describe la resolución de un punto de interrupción de error, incluida la ubicación, el programa y subproceso.  
  
 [BP_LOCATION](../../../extensibility/debugger/reference/bp-location.md)  
 Especifica el tipo de estructura que se utiliza para describir la ubicación del punto de interrupción.  
  
 [BP_LOCATION_CODE_ADDRESS](../../../extensibility/debugger/reference/bp-location-code-address.md)  
 Define los componentes que describen la ubicación de un punto de interrupción en una dirección en el código.  
  
 [BP_LOCATION_CODE_CONTEXT](../../../extensibility/debugger/reference/bp-location-code-context.md)  
 Describe la ubicación de un punto de interrupción que se enlaza directamente a una dirección en el programa que se está depurando.  
  
 [BP_LOCATION_CODE_FILE_LINE](../../../extensibility/debugger/reference/bp-location-code-file-line.md)  
 Describe la ubicación de un punto de interrupción en la línea de un archivo de código fuente.  
  
 [BP_LOCATION_CODE_FUNC_OFFSET](../../../extensibility/debugger/reference/bp-location-code-func-offset.md)  
 Describe la ubicación de desplazamiento de un punto de interrupción en una función en código.  
  
 [BP_LOCATION_CODE_STRING](../../../extensibility/debugger/reference/bp-location-code-string.md)  
 Se usa para establecer puntos de interrupción de código basados en una cadena que el usuario puede escribir desde el IDE.  
  
 [BP_LOCATION_DATA_STRING](../../../extensibility/debugger/reference/bp-location-data-string.md)  
 Se usa para establecer puntos de interrupción de datos que se basan en una cadena que el usuario puede escribir desde el IDE.  
  
 [BP_LOCATION_RESOLUTION](../../../extensibility/debugger/reference/bp-location-resolution.md)  
 Describe la resolución de un punto de interrupción en una ubicación específica.  
  
 [BP_PASSCOUNT](../../../extensibility/debugger/reference/bp-passcount.md)  
 Describe el número y las condiciones en la que se desencadenará un punto de interrupción después de tener previamente se ha pasado.  
  
 [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md)  
 Contiene la información necesaria para implementar un punto de interrupción.  
  
 [BP_REQUEST_INFO2](../../../extensibility/debugger/reference/bp-request-info2.md)  
 Contiene la información necesaria para implementar un punto de interrupción (igual que el [BP_REQUEST_INFO](../../../extensibility/debugger/reference/bp-request-info.md) estructura, pero incluye información de GUID, la restricción y punto de seguimiento del proveedor).  
  
 [BP_RESOLUTION_CODE](../../../extensibility/debugger/reference/bp-resolution-code.md)  
 Describe la ubicación de un punto de interrupción del código.  
  
 [BP_RESOLUTION_DATA](../../../extensibility/debugger/reference/bp-resolution-data.md)  
 Describe el resultado de un punto de interrupción de datos de enlace.  
  
 [BP_RESOLUTION_INFO](../../../extensibility/debugger/reference/bp-resolution-info.md)  
 Describe la información de punto de interrupción enlazado para un punto de interrupción de código o un punto de interrupción de datos.  
  
 [BP_RESOLUTION_LOCATION](../../../extensibility/debugger/reference/bp-resolution-location.md)  
 Especifica la estructura de la ubicación de la resolución de punto de interrupción.  
  
 [BSTR_ARRAY](../../../extensibility/debugger/reference/bstr-array.md)  
 Describe una matriz de cadenas.  
  
 [BUILT_TYPE](../../../extensibility/debugger/reference/built-type.md)  
 Especifica información sobre un tipo de campo que se toman de los metadatos.  
  
 [CODE_PATH](../../../extensibility/debugger/reference/code-path.md)  
 Describe una llamada a una función o método.  
  
 [COMPUTER_INFO](../../../extensibility/debugger/reference/computer-info.md)  
 Se describe en el equipo donde se ejecuta el depurador.  
  
 [CONST_GUID_ARRAY](../../../extensibility/debugger/reference/const-guid-array.md)  
 Describe una lista de GUID.  
  
 [CONTEXT_INFO](../../../extensibility/debugger/reference/context-info.md)  
 Describe un contexto de la memoria o el contexto del código.  
  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)  
 Describe una dirección en un programa que se está depurando.  
  
 [DEBUG_ADDRESS_UNION](../../../extensibility/debugger/reference/debug-address-union.md)  
 Representa una cantidad de diferentes tipos de direcciones.  
  
 [DEBUG_CUSTOM_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md)  
 Identifica un visor personalizado o tipo de visualizador.  
  
 [DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md)  
 Describe una propiedad de depuración que a su vez describe un objeto de una naturaleza jerárquica que tiene el nombre, tipo y valor.  
  
 [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md)  
 Describe una referencia.  
  
 [DisassemblyData](../../../extensibility/debugger/reference/disassemblydata.md)  
 Describe el desensamblado en el IDE para su presentación.  
  
 [EXCEPTION_INFO](../../../extensibility/debugger/reference/exception-info.md)  
 Describe una excepción o error de tiempo de ejecución producido por el programa que se está depurando.  
  
 [FIELD_INFO](../../../extensibility/debugger/reference/field-info.md)  
 Describe una variable local, parámetro u otro campo.  
  
 [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md)  
 Describe un marco de pila.  
  
 [GUID_ARRAY](../../../extensibility/debugger/reference/guid-array.md)  
 Describe una matriz de identificadores únicos para los motores de depuración disponible.  
  
 [JMC_CODE_SPEC](../../../extensibility/debugger/reference/jmc-code-spec.md)  
 Se usa para establecer la información de JustMyCode de un módulo.  
  
 [MACHINE_INFO](../../../extensibility/debugger/reference/machine-info.md)  
 Describe un equipo determinado.  
  
 [METADATA_ADDRESS_ARRAYELEM](../../../extensibility/debugger/reference/metadata-address-arrayelem.md)  
 Describe un elemento de matriz dentro de una matriz.  
  
 [METADATA_ADDRESS_FIELD](../../../extensibility/debugger/reference/metadata-address-field.md)  
 Describe la dirección de un campo de una clase o estructura.  
  
 [METADATA_ADDRESS_LOCAL](../../../extensibility/debugger/reference/metadata-address-local.md)  
 Describe la dirección de una variable local dentro de un ámbito (normalmente una función o método).  
  
 [METADATA_ADDRESS_METHOD](../../../extensibility/debugger/reference/metadata-address-method.md)  
 Describe la dirección de un método de una clase.  
  
 [METADATA_ADDRESS_PARAM](../../../extensibility/debugger/reference/metadata-address-param.md)  
 Describe un parámetro de un método o función.  
  
 [METADATA_ADDRESS_RETVAL](../../../extensibility/debugger/reference/metadata-address-retval.md)  
 Describe un valor devuelto de un método o función.  
  
 [METADATA_TYPE](../../../extensibility/debugger/reference/metadata-type.md)  
 Describe un tipo de campo que se toman de los metadatos.  
  
 [MODULE_INFO](../../../extensibility/debugger/reference/module-info.md)  
 Describe un módulo determinado (ensamblado, EXE o DLL).  
  
 [MODULE_SYMBOL_SEARCH_INFO](../../../extensibility/debugger/reference/module-symbol-search-info.md)  
 Describe la información de estado sobre las rutas de acceso de búsqueda de símbolos que se ha buscado.  
  
 [NATIVE_ADDRESS](../../../extensibility/debugger/reference/native-address.md)  
 Describe una dirección nativa.  
  
 [PDB_TYPE](../../../extensibility/debugger/reference/pdb-type.md)  
 Describe un tipo de campo realizado desde un símbolo PDB.  
  
 [PENDING_BP_STATE_INFO](../../../extensibility/debugger/reference/pending-bp-state-info.md)  
 Describe el estado de un punto de interrupción que está listo para enlazar a una ubicación del código.  
  
 [PROCESS_INFO](../../../extensibility/debugger/reference/process-info.md)  
 Describe un proceso.  
  
 [PROGRAM_NODE_ARRAY](../../../extensibility/debugger/reference/program-node-array.md)  
 Describe una lista de [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) objetos que representan nodos de programa.  
  
 [PROVIDER_PROCESS_DATA](../../../extensibility/debugger/reference/provider-process-data.md)  
 Describe los procesos que se ejecutan en un equipo.  
  
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)  
 Describe la ubicación de línea y columna en el texto dado.  
  
 [THREADPROPERTIES](../../../extensibility/debugger/reference/threadproperties.md)  
 Describe las propiedades de un subproceso.  
  
 [TYPE_INFO](../../../extensibility/debugger/reference/type-info.md)  
 Describe un tipo de campo.  
  
 [UNMANAGED_ADDRESS_PHYSICAL](../../../extensibility/debugger/reference/unmanaged-address-physical.md)  
 Describe una dirección física.  
  
 [UNMANAGED_ADDRESS_THIS_RELATIVE](../../../extensibility/debugger/reference/unmanaged-address-this-relative.md)  
 Describe una dirección que es relativa a un `this` puntero (`Me` en Visual Basic).  
  
## <a name="requirements"></a>Requisitos  
 Encabezado: msdbg.h, sh.h o ee.h  
  
 Espacio de nombres:  Microsoft.VisualStudio.Debugger.Interop  
  
 Ensamblado: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vea también  
 [Referencia de API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
