---
title: Resolución de ensamblados en tiempo de diseño | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: msbuild
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 920e7222b3b425cbb13c962ff8c2e1e2fc551bd8
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "68159230"
---
# <a name="resolving-assemblies-at-design-time"></a>Resolver ensamblados en tiempo de diseño
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Cuando se agrega una referencia a un ensamblado mediante la pestaña .NET del cuadro de diálogo Agregar referencia, la referencia señala a un ensamblado de referencia intermedio, es decir, un ensamblado que contiene toda la información de firma y de tipos, pero que no contiene código necesariamente. La pestaña .NET hace una lista de los ensamblados de referencia que corresponden a los ensamblados en tiempo de ejecución en .NET Framework. Además, hace una lista de los ensamblados de referencia que corresponden a los ensamblados en tiempo de ejecución de las carpetas AssemblyFoldersEx que utilizan otros fabricantes.  
  
## <a name="multi-targeting"></a>Compatibilidad con múltiples versiones (multi-targeting)  
 [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] permite tener como destino las versiones de .NET Framework que se ejecutan en la versión 2.0 o la versión 4 de Common Language Runtime (CLR). Esto incluye las versiones 2.0, 3.0, 3.5, 4, 4.5 y 4.5.1 de .NET Framework y las versiones 1.0, 2.0 y 3.0 de Silverlight. Si se publica una nueva versión de .NET Framework que está basada en la versión 2.0 o la versión 4 de CLR, Framework se puede instalar utilizando un paquete de destino, que se presentará automáticamente como destino en Visual Studio.  
  
## <a name="how-type-resolution-works"></a>Cómo funciona la resolución de tipos  
 En tiempo de ejecución, el CLR resuelve los tipos del ensamblado buscando en la GAC, el directorio bin y en cualquiera de las rutas de acceso de sondeo. De esto se ocupa el cargador de ensamblados Fusion. Pero, ¿cómo identifica el cargador lo que está buscando? Esto depende de una resolución hecha en tiempo de diseño, cuando se compila la aplicación.  
  
 Durante la compilación, el compilador resuelve los tipos de aplicación utilizando los ensamblados de referencia. En las versiones 2.0, 3.0, 3.5, 4, 4.5 y 4.5.1 de .NET Framework, los ensamblados de referencia se instalan cuando se instala .NET Framework.  
  
 Los ensamblados de referencia los proporciona el paquete de destino que se distribuye con la versión correspondiente de .NET Framework SDK. El Framework proporciona solo los ensamblados en tiempo de ejecución. Para compilar aplicaciones, necesita instalar .NET Framework y el SDK correspondiente.  
  
 Cuando tiene como destino una versión de .NET Framework concreta, el sistema de compilación resuelve todos los tipos utilizando los ensamblados de referencia del paquete de destino. En tiempo de ejecución, el cargador resuelve estos mismos tipos con los ensamblados en tiempo de ejecución, que se encuentran normalmente en la GAC.  
  
 Si los ensamblados de referencia no están disponibles, el sistema de compilación resuelve los tipos utilizando los ensamblados en tiempo de ejecución. Dado que los ensamblados en tiempo de ejecución de la GAC no se distinguen por los números de versión secundaria, es posible que la resolución se lleve a cabo con el ensamblado equivocado. Por ejemplo, esto podría pasar si se hace referencia a un método de .NET Framework nuevo en la versión 3.5 mientras que la versión de destino es la 3.0. La compilación tendrá éxito y la aplicación se ejecutará en la máquina de compilación, pero dará error cuando se implemente en una máquina que no tenga instalada la versión 3.5.  
  
 El paquete de destino que ahora se distribuye con .NET Framework SDK incluye una lista de todos los ensamblados en tiempo de ejecución de esa versión de Framework, llamada lista de redistribuciones (redist). Esto hace imposible que el sistema de compilación resuelva los tipos con una versión equivocada del ensamblado.  
  
## <a name="see-also"></a>Otras referencias  
 [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)
