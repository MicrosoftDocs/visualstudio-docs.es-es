---
title: Active Script Debugger (constantes), enumeraciones y estructuras | Documentos de Microsoft
ms.custom: ''
ms.date: 01/18/2017
ms.prod: windows-script-interfaces
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugger structures
- Active Script Debugger enumerations
- Active Script Debugger constants
ms.assetid: b80b9207-fb19-4ee2-85fb-41f8c26e7706
caps.latest.revision: 13
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 913c1b243bcc9c7a6653025fbfcb4f941df2950e
ms.sourcegitcommit: 8bf9e51c77a5a602fab9513b9187e59e57dfebad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/16/2019
ms.locfileid: "54345440"
---
# <a name="active-script-debugger-constants-enumerations-and-structures"></a>Active Script Debugger (Constantes, enumeraciones y estructuras)
Las interfaces de depuración activa utilizan las constantes, enumeraciones y estructuras siguientes.  
  
## <a name="constants-enumerations-and-structures"></a>Constantes, enumeraciones y estructuras  
  
|Constantes|Descripción|  
|---------------|-----------------|  
|[APPBREAKFLAGS (constantes)](../../winscript/reference/appbreakflags-enumeration.md)|Indican el estado de depuración actual de aplicaciones y subprocesos.|  
|[DEBUG_TEXT (Constantes)](../../winscript/reference/debug-text-constants.md)|Marcas de opción utilizadas durante [IDebugExpressionContext::ParseLanguageText](../../winscript/reference/idebugexpressioncontext-parselanguagetext.md).|  
|[TEXT_DOC_ATTR (Constantes)](../../winscript/reference/text-doc-attr-constants.md)|Describen los atributos del documento.|  
  
|Enumeraciones|Descripción|  
|------------------|-----------------|  
|[APPBREAKFLAGS (constantes)](../../winscript/reference/appbreakflags-enumeration.md)|Indican el estado de depuración actual de aplicaciones y subprocesos.|  
|[APPLICATION_NODE_EVENT_FILTER (Enumeración)](../../winscript/reference/application-node-event-filter-enumeration.md)|Indican los nodos que se excluirán con un filtro.|  
|[BREAKPOINT_STATE (Enumeración)](../../winscript/reference/breakpoint-state-enumeration.md)|Indica el estado de un punto de interrupción.|  
|[BREAKREASON (Enumeración)](../../winscript/reference/breakreason-enumeration.md)|Indica qué produjo la interrupción.|  
|[BREAKRESUMEACTION (Enumeración)](../../winscript/reference/breakresumeaction-enumeration.md)|Describe cómo continuar desde un punto de interrupción.|  
|[DOCUMENTNAMETYPE (Enumeración)](../../winscript/reference/documentnametype-enumeration.md)|Describe qué tipo se va a obtener para un documento.|  
|[ERRORRESUMEACTION (Enumeración)](../../winscript/reference/errorresumeaction-enumeration.md)|Describe cómo continuar desde un error de tiempo de ejecución.|  
|[JS_PROPERTY_ATTRIBUTES (Enumeración)](../../winscript/reference/js-property-attributes-enumeration.md)|Indica los atributos de una propiedad.|  
|[JS_PROPERTY_MEMBERS (Enumeración)](../../winscript/reference/js-property-members-enumeration.md)|Marcas para especificar el tipo de información que se va a devolver en una solicitud de miembros de un objeto.|  
|[JsDebugReadMemoryFlags (Enumeración)](../../winscript/reference/jsdebugreadmemoryflags-enumeration.md)|Marcas para especificar el comportamiento al leer la memoria.|  
|[SCRIPT_DEBUGGER_OPTIONS (Enumeración)](../../winscript/reference/script-debugger-options-enumeration.md)|Indica un conjunto de opciones o capacidades que se aplican al depurador adjunto.|  
|[SCRIPT_ERROR_DEBUG_EXCEPTION_THROWN_KIND (Enumeración)](../../winscript/reference/script-error-debug-exception-thrown-kind-enumeration.md)|Indica la clase de excepción producida.|  
|[SOURCE_TEXT_ATTR (constantes)](../../winscript/reference/source-text-attr-enumeration.md)|Describen los atributos de un carácter individual del texto de origen.|  
  
|Estructuras|Descripción|  
|----------------|-----------------|  
|[DebugStackFrameDescriptor (Estructura)](../../winscript/reference/debugstackframedescriptor-structure.md)|Enumera los marcos de pila y la salida de las combinaciones de varios enumeradores en el mismo subproceso.|  
|[JS_NATIVE_FRAME (Estructura)](../../winscript/reference/js-native-frame-structure.md)|Representa un marco de pila.|  
|[JsDebugPropertyInfo (Estructura)](../../winscript/reference/jsdebugpropertyinfo-structure.md)|Indica información sobre una propiedad.|  
|[TEXT_DOCUMENT_ARRAY (Estructura)](../../winscript/reference/text-document-array-structure.md)|Proporciona un conjunto de documentos.|