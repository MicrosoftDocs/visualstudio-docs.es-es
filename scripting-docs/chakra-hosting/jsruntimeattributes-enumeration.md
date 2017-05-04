---
title: "JsRuntimeAttributes (Enumeraci&#243;n) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "jsrt/JsRuntimeAttributes"
helpviewer_keywords: 
  - "JsRuntimeAttributes (enumeración)"
ms.assetid: f76d82e9-a695-4d6a-96c1-b3a4d27fed68
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# JsRuntimeAttributes (Enumeraci&#243;n)
Atributos de un runtime.  
  
## Sintaxis  
  
```  
enum JsRuntimeAttributes;  
```  
  
## Miembros  
  
### Valores  
  
|Nombre|Descripción|  
|------------|-----------------|  
|`JsRuntimeAttributeAllowScriptInterrupt`|El runtime debe admitir la interrupción confiable de scripts. Esto incrementa el número de lugares donde el runtime buscará una solicitud de interrupción del script a costa de una pequeña sobrecarga en el rendimiento del runtime.|  
|`JsRuntimeAttributeDisableBackgroundWork`|El runtime no realizará ninguna tarea \(como la recolección de elementos no utilizados\) en subprocesos en segundo plano.|  
|`JsRuntimeAttributeDisableEval`|El uso del constructor `eval` o `function` producirá una excepción.|  
|`JsRuntimeAttributeDisableNativeCodeGeneration`|El runtime no generará código nativo.|  
|`JsRuntimeAttributeEnableExperimentalFeatures`|El runtime permitirá todas las características experimentales.|  
|`JsRuntimeAttributeEnableIdleProcessing`|El host llamará a `JsIdle` para habilitar el procesamiento en inactividad. De lo contrario, el runtime administrará la memoria de una forma ligeramente más agresiva.|  
|`JsRuntimeAttributeDispatchSetExceptionsToDebugger`|La llamada a `JsSetException` también enviará la excepción al depurador de scripts \(si lo hubiera\), lo que le permite al depurador detenerse en la excepción.|  
|`JsRuntimeAttributeNone`|Ningún atributo especial.|  
  
## Requisitos  
 **Encabezado:** jsrt.h  
  
## Vea también  
 [Referencia \(Runtime de JavaScript\)](../chakra-hosting/reference-javascript-runtime.md)