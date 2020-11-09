---
title: Resolución de ensamblados en tiempo de diseño | Microsoft Docs
description: Obtenga información sobre cómo MSBuild resuelve las referencias a ensamblados en tiempo de diseño mediante el uso de ensamblados de referencia en el paquete de destino.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild
ms.assetid: 20dae076-733e-49c1-a2e9-b336757ae21d
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 515c99a4d73abcb3a287f3f4026723bd8050b360
ms.sourcegitcommit: 1a36533f385e50c05f661f440380fda6386ed3c1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/30/2020
ms.locfileid: "93048487"
---
# <a name="resolve-assemblies-at-design-time"></a>Resolución de ensamblados en tiempo de diseño

Cuando se agrega una referencia a un ensamblado mediante la pestaña **.NET** del cuadro de diálogo **Agregar referencia** , la referencia señala a un ensamblado de referencia intermedio, es decir, un ensamblado que contiene toda la información de firma y de tipos, pero que no contiene código necesariamente. La pestaña **.NET** enumera los ensamblados de referencia que corresponden a los ensamblados en tiempo de ejecución en .NET Framework. Además, enumera los ensamblados de referencia que corresponden a los ensamblados en tiempo de ejecución de las carpetas AssemblyFoldersEx que utilizan otros fabricantes.

## <a name="multi-targeting"></a>Compatibilidad con múltiples versiones

 Visual Studio le permite tener como destino las versiones de .NET Framework que se ejecutan en varias versiones de .NET Framework. Si se publica una nueva versión de .NET Framework, Framework se puede instalar utilizando un paquete de destino, que se presentará automáticamente como destino en Visual Studio.

## <a name="how-type-resolution-works"></a>Cómo funciona la resolución de tipos

 En tiempo de ejecución, el CLR resuelve los tipos del ensamblado. Para ello, busca en la caché global de ensamblados, el directorio *bin* y en cualquiera de las rutas de acceso de sondeo. De esto se ocupa el cargador de ensamblados Fusion. Pero, ¿cómo identifica el cargador lo que está buscando? Depende una resolución realizada en tiempo de diseño, cuando se compila la aplicación.

 Durante la compilación, el compilador resuelve los tipos de aplicación utilizando los ensamblados de referencia. En las versiones de .NET Framework 2.0, 3.0, 3.5, 4, 4.5 y 4.5.1, los ensamblados de referencia se instalan cuando se instala .NET Framework.

 Los ensamblados de referencia los proporciona el paquete de destino que se distribuye con la versión correspondiente de .NET Framework SDK. El Framework proporciona solo los ensamblados en tiempo de ejecución. Para compilar aplicaciones, necesita instalar .NET Framework y el SDK correspondiente.

 Cuando tiene como destino una versión de .NET Framework concreta, el sistema de compilación resuelve todos los tipos utilizando los ensamblados de referencia del paquete de destino. En tiempo de ejecución, el cargador resuelve estos mismos tipos con los ensamblados en tiempo de ejecución, que se encuentran normalmente en la caché global de ensamblados.

 Si los ensamblados de referencia no están disponibles, el sistema de compilación resuelve los tipos utilizando los ensamblados en tiempo de ejecución. Dado que los ensamblados en tiempo de ejecución de la GAC no se distinguen por los números de versión secundaria, es posible que la resolución se lleve a cabo con el ensamblado equivocado. Por ejemplo, esto podría pasar si se hace referencia a un método de .NET Framework nuevo en la versión 3.5 mientras que la versión de destino es la 3.0. La compilación tendrá éxito y la aplicación se ejecutará en la máquina de compilación, pero dará error cuando se implemente en una máquina que no tenga instalada la versión 3.5.

 El paquete de destino que ahora se distribuye con el SDK de .NET Framework incluye una lista de todos los ensamblados en tiempo de ejecución en esa versión de Framework, llamada lista de redistribución (redist), lo que hace imposible que el sistema de compilación resuelva los tipos con la versión incorrecta del ensamblado.

## <a name="see-also"></a>Vea también
- [Conceptos avanzados](../msbuild/msbuild-advanced-concepts.md)
