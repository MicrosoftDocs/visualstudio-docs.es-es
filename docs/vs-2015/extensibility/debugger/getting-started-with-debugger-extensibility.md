---
title: Introducción a extensibilidad del depurador | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- getting started, Debugging SDK
- debugging [Debugging SDK], getting started
- Debugging SDK, getting started
ms.assetid: d6ce6f43-1409-4bf7-93cd-f3464ca23504
caps.latest.revision: 18
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: bafdd45b57a9fe660e97127c2c99c333ead0e60a
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51721168"
---
# <a name="getting-started-with-debugger-extensibility"></a>Introducción a la extensibilidad del depurador
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)] proporciona la información que debe tener para crear y personalizar los componentes del depurador para depurar programas desde el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] entorno.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuración ha agregado mejoras que se deriva de la facilidad de uso extenso las pruebas realizadas en anteriores [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuradores. Puede usar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depuración paso a través de una aplicación de varios idioma, o puede implementar en marcha de edición de las variables durante la depuración de aplicaciones y soluciones de varios idiomas.  
  
 [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] la depuración es ejecutada fuera de proceso con el programa que se está depurando y, por tanto, es menos intrusiva en el espacio de proceso de la aplicación. Por lo tanto, es más fácil escribir componentes que interactúan con el depurador sin que afecte a su programa de depuración.  
  
 Mejor forma de usar el [!INCLUDE[vsipsdk](../../includes/vsipsdk-md.md)], debe estar familiarizado con lo siguiente:  
  
-   El [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] el entorno de desarrollo integrado (IDE)  
  
-   El lenguaje de programación de C++  
  
-   COM DE ATL  
  
## <a name="in-this-section"></a>En esta sección  
 [Guía básica para ampliar el depurador](../../extensibility/debugger/roadmap-for-extending-the-debugger.md)  
 Describe el proceso de implementación de depuración en su producto, según el compilador y su salida.  
  
 [Componentes del depurador](../../extensibility/debugger/debugger-components.md)  
 Proporciona información general sobre el [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] depurar componentes, que se incluyen el motor de depuración (DE), el evaluador de expresiones (EE) y el controlador de símbolos (SH).  
  
 [Conceptos del depurador](../../extensibility/debugger/debugger-concepts.md)  
 Describe los principales conceptos de arquitectura de depuración.  
  
 [Contextos de depurador](../../extensibility/debugger/debugger-contexts.md)  
 Explica cómo el motor de depuración (DE) funciona simultáneamente dentro de código, documentación y contextos de evaluación de expresión. Se describen para cada uno de los tres contextos, la ubicación, posición o evaluación pertinente a él.  
  
 [Tareas de depuración](../../extensibility/debugger/debugging-tasks.md)  
 Contiene vínculos a diversas tareas de depuración, como iniciar un programa y evaluar expresiones.

