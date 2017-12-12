---
title: "Enumeración JsErrorCode | Microsoft Docs"
ms.custom: 
ms.date: 01/18/2017
ms.prod: windows-client-threshold
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: jsrt/JsErrorCode
helpviewer_keywords: JsErrorCode enumeration
ms.assetid: 4902f3f3-47a5-4e74-9c29-f96eeecbcda9
caps.latest.revision: "15"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: b09babd38505c5619f414d2e349cd52b3596ceac
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/27/2017
---
# <a name="jserrorcode-enumeration"></a>JsErrorCode (Enumeración)
Código de error devuelto desde una API de hospedaje de Chakra.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
enum JsErrorCode : unsigned int;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="values"></a>Valores  
  
|Nombre|Descripción|  
|----------|-----------------|  
|`JsErrorAlreadyDebuggingContext`|El contexto no se puede poner en estado de depuración porque ya se encuentra en dicho estado.|  
|`JsErrorAlreadyProfilingContext`|El contexto no puede iniciar la generación de perfiles porque ya la está realizando.|  
|`JsErrorArgumentNotObject`|Se ha llamado a una API de hospedaje que funciona con valores de objeto con un valor que no es un objeto.|  
|`JsErrorBadSerializedScript`|Se usó un script serializado incorrecto, o el script serializado lo serializó otra versión del motor de Chakra.|  
|`JsErrorCannotDisableExecution`|El runtime no admite la interrupción confiable de scripts.|  
|`JsErrorCannotSerializeDebugScript`|Los scripts no se pueden serializar en contextos de depuración.|  
|`JsErrorCategoryEngine`|Categoría de errores relacionada con los errores que aparecen en el propio motor.|  
|`JsErrorCategoryFatal`|Categoría de errores graves y que implican un error del motor.|  
|`JsErrorCategoryScript`|Categoría de errores relacionada con los errores de un script.|  
|`JsErrorCategoryUsage`|Categoría de errores relacionada con el uso incorrecto de la propia API.|  
|`JsErrorFatal`|Se ha producido un error irrecuperable en el motor.|  
|`JsErrorHeapEnumInProgress`|Hay una enumeración del montón actualmente en curso en el contexto del script.|  
|`JsErrorIdleNotEnabled`|Notificación de inactividad proporcionada cuando el host no habilitó el procesamiento en inactividad.|  
|`JsErrorInDisabledState`|El runtime se encuentra en estado deshabilitado.|  
|`JsErrorInExceptionState`|El motor está en un estado de excepción y no se puede llamar a ninguna API hasta que se borre la excepción.|  
|`JsErrorInObjectBeforeCollectCallback`|La operación no se admite en un objeto antes de recopilar una devolución de llamada.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsErrorInProfileCallback`|Un contexto de script está en medio de una devolución de llamada del perfil.|  
|`JsErrorInThreadServiceCallback`|Hay una devolución de llamada del servicio del subproceso actualmente en curso.|  
|`JsErrorInvalidArgument`|Un argumento para una API de hospedaje no era válido.|  
|`JsErrorNoCurrentContext`|La API de hospedaje requiere que haya un contexto actual, pero no hay ninguno.|  
|`JsErrorNotImplemented`|Aún no se ha implementado una API de hospedaje.|  
|`JsErrorNullArgument`|Un argumento de la API de hospedaje era NULL en un contexto donde este valor no está permitido.|  
|`JsErrorObjectNotInspectable`|No se puede desajustar el objeto para el puntero `IInspectable` .<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsErrorOutOfMemory`|El motor de Chakra se ha quedado sin memoria.|  
|`JsErrorPropertyNotSymbol`|API de hospedaje que funciona en los identificadores de propiedad de símbolo, pero que se llamó con un identificador de propiedad que no es un símbolo. El código de error devuelto por `JsGetSymbolFromPropertyId` si se llama a la función con un identificador de propiedad que no es un símbolo.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsErrorPropertyNotString`|API de hospedaje que funciona en los identificadores de propiedad de cadena, pero que se llamó con un identificador de propiedad que no es una cadena. El código de error devuelto por `JsGetPropertyNamefromId` existente si se llama a la función con un identificador de propiedad que no es una cadena.<br /><br /> Este valor de enumeración solo se admite en modo de borde.|  
|`JsErrorRuntimeInUse`|No se puede desechar un runtime que aún está en uso.|  
|`JsErrorScriptCompile`|Error al compilar JavaScript.|  
|`JsErrorScriptEvalDisabled`|Un script finalizó porque intentó usar `eval` o `function` y eval se deshabilitó.|  
|`JsErrorScriptException`|Se produjo una excepción de JavaScript durante la ejecución de un script.|  
|`JsErrorScriptTerminated`|Un script finalizó debido a una solicitud para suspender un runtime.|  
|`JsErrorWrongRuntime`|Se llamó a una API de hospedaje mediante los objetos creados en un tiempo de ejecución de JavaScript diferente.|  
|`JsErrorWrongThread`|Se llamó a una API de hospedaje en el subproceso equivocado.|  
|`JsNoError`|Código de error de operación correcta.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** jsrt.h  
  
## <a name="see-also"></a>Vea también  
 [Referencia (tiempo de ejecución de JavaScript)](../chakra-hosting/reference-javascript-runtime.md)