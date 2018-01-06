---
title: "Introducción a la extensibilidad del depurador | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 964b6bcc18e74174aa59e7a1bb4441e24d3918d7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="getting-started-with-debugger-extensibility"></a>Introducción a la extensibilidad del depurador
El [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] proporciona la información que necesita para crear y personalizar los componentes del depurador permite depurar programas desde la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] entorno.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuración ha agregado mejoras que se deriva de la facilidad de uso extenso pruebas realizadas en anteriores [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depuradores. Puede usar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la depuración en el paso a través de una aplicación de varios idioma, o puede implementar en marcha de edición de variables durante la depuración de aplicaciones y soluciones de varios idiomas.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]depuración es ejecutado fuera de proceso con el programa que se está depurando y, por tanto, es menos intrusiva en el espacio de proceso de la aplicación. Por lo tanto, es más fácil escribir componentes que interactúan con el depurador sin que afecte a su programa de depuración.  
  
 Utilizar mejor el [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)], debe estar familiarizado con lo siguiente:  
  
-   El [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE)  
  
-   El lenguaje de programación de C++  
  
-   COM DE ATL  
  
## <a name="in-this-section"></a>En esta sección  
 [Guía básica para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Se describe el proceso de implementación de depuración en su producto, según el compilador y sus resultados.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] depurar componentes, que incluyen el motor de depuración (Alemania), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor de depuración (Alemania) funciona simultáneamente dentro de código, documentación y los contextos de evaluación de expresión. Describe, para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a varias tareas de depuración, como iniciar un programa y la evaluación de expresiones.