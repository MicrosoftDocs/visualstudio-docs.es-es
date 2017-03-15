---
title: "Gu&#237;a b&#225;sica para ampliar el depurador | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "depurar [SDK de depuración], plan"
  - "SDK de depuración, la guía básica"
ms.assetid: 1f4096a8-f7aa-4dfa-84e1-6d59263e70bb
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Gu&#237;a b&#225;sica para ampliar el depurador
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Esta documentación se proporciona la información de la guía y de referencia para extender el depurador de [!INCLUDE[vs_current_short](../../code-quality/includes/vs_current_short_md.md)] con [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)].  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depura la documentación incluye ejemplos, una referencia completa, y varios escenarios representativas que muestran maneras típicas de personalizar el depurador.  
  
 El compilador y el resultado determinan lo que necesita hacer para implementar la depuración en el producto.  si el compilador:  
  
-   Destina el sistema operativo nativo de Windows y escribe un archivo .PDB, puede programas de depuración con el motor de depuración de código nativo \(DE\), que está integrado en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  No necesita implementar un OF o un evaluador de expresiones.  Escriba el evaluador de expresiones para la sintaxis del lenguaje de programación de C\+\+.  
  
-   Genera el lenguaje intermedio de Microsoft \(MSIL\) generado, puede programas de depuración con el motor De depuración de código administrado, que también se integra en [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  Así, solo necesita implementar un evaluador de expresiones.  Proporcionan un evaluador de expresiones de ejemplo para usted.  Para obtener más información, vea los temas siguientes:  
  
     [Evaluación de expresiones](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
  
     [Evaluar expresiones](../../extensibility/debugger/evaluating-expressions.md)  
  
     [Contexto de la evaluación de expresiones](../../extensibility/debugger/expression-evaluation-context.md)  
  
     [Evaluación de expresiones en modo de interrupción](../../extensibility/debugger/expression-evaluation-in-break-mode.md)  
  
     [Escribir una expresión Evaluador de Common Language Runtime](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)  
  
-   Es un sistema operativo propietario o algún otro entorno en tiempo de ejecución, debe escribir dispone del DE.  Se proporciona un tutorial que crea un OF simple mediante ATL COM.  Para obtener más información, vea los temas siguientes:  
  
     [Crear un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)  
  
     [tutorial: Compilar un motor Utilizar ATL COM de depuración](http://msdn.microsoft.com/es-es/9097b71e-1fe7-48f7-bc00-009e25940c24)  
  
     [Implementar un proveedor de puerto](../../extensibility/debugger/implementing-a-port-supplier.md)  
  
     [Muestras](../../extensibility/debugger/visual-studio-debugging-samples.md)  
  
## Vea también  
 [Introducción](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)