---
title: "Cambiar el valor de una variable Local | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], la evaluación de expresiones"
  - "evaluación de expresiones, cambiar los valores mediante programación"
ms.assetid: 8407d3df-d38a-4328-82d1-98084bef43ec
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Cambiar el valor de una variable Local
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

> [!IMPORTANT]
>  En Visual Studio 2015, esta forma de implementar los evaluadores de expresión está obsoleta. Para obtener información sobre la implementación de evaluadores de expresión de CLR, vea [evaluadores de expresiones CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) y [ejemplo de evaluador de expresiones administrado](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Cuando se escribe un nuevo valor en el campo de valor de la **locales** ventana, el paquete de depuración pasa la cadena, como se escribió en el evaluador de expresiones \(EE\). EE evalúa esta cadena, que puede contener un valor simple o una expresión y almacena el valor resultante en la variable local asociada.  
  
 Se trata de una visión general del proceso de cambiar el valor de una variable local:  
  
1.  Cuando el usuario introduce el nuevo valor, Visual Studio llama a [SetValueAsString](../../extensibility/debugger/reference/idebugproperty2-setvalueasstring.md) en la [IDebugProperty2](../../extensibility/debugger/reference/idebugproperty2.md) objeto asociado con el equipo local.  
  
2.  `IDebugProperty2::SetValueAsString` realiza las tareas siguientes:  
  
    1.  Evalúa la cadena para generar un valor.  
  
    2.  Enlaza asociado [IDebugField](../../extensibility/debugger/reference/idebugfield.md) objeto que se va a obtener un [IDebugObject](../../extensibility/debugger/reference/idebugobject.md) objeto.  
  
    3.  Convierte el valor en una serie de bytes.  
  
    4.  Llamadas [SetValue](../../extensibility/debugger/reference/idebugobject-setvalue.md) poner bytes del valor en la memoria para el programa que se está depurando pueda acceder a ellos.  
  
3.  Visual Studio actualiza el **locales** mostrar \(consulte [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md) para obtener más información\).  
  
 Este procedimiento también se utiliza para cambiar el valor de una variable en el **inspección** ventana excepto si es la `IDebugProperty2` objeto asociado con el valor de la variable local que se utiliza en lugar de la `IDebugProperty2` objeto asociado a la variable local propio.  
  
## En esta sección  
 [Implementación de cambiar los valores de ejemplo](../../extensibility/debugger/sample-implementation-of-changing-values.md)  
 Utiliza el ejemplo MyCEE paso a paso por el proceso de cambiar los valores.  
  
## Vea también  
 [Escribir un evaluador de expresiones de CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)   
 [Mostrar variables locales](../../extensibility/debugger/displaying-locals.md)