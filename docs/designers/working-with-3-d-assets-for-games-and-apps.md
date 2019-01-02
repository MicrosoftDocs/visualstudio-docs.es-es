---
title: Trabajo con recursos en 3D para juegos y aplicaciones
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
f1_keywords:
- vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: fd9aa8cc571ba58964346ca85a62b7ec311a744a
ms.sourcegitcommit: f6dd17b0864419083d0a1bf54910023045526437
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/27/2018
ms.locfileid: "53803667"
---
# <a name="work-with-3d-assets-for-games-and-apps"></a>Trabajar con recursos en 3D para juegos y aplicaciones

En este documento, se describen las herramientas de Visual Studio que puede usar para crear o modificar modelos 3D, texturas y sombreadores para aplicaciones y juegos basados en DirectX.

## <a name="directx-app-development-in-visual-studio"></a>Desarrollo de aplicaciones de DirectX en Visual Studio
 Normalmente, una aplicación de DirectX combina lógica de programación, la API de DirectX y programas de lenguaje de sombreado de alto nivel (HLSL), junto con recursos visuales 3D y de audio para presentar una experiencia multimedia enriquecida e interactiva. Visual Studio incluye herramientas para trabajar con imágenes y texturas, modelos 3D y sombreadores sin salir del IDE para usar otra herramienta. Las herramientas de Visual Studio son especialmente adecuadas para crear activos de *marcador de posición*, que sirven para probar el código o compilar prototipos antes de programar activos listos para producción, y para inspeccionar y modificar activos listos para producción cuando depura la aplicación.

 Aquí tiene más información sobre los tipos de recursos con los que puede trabajar en Visual Studio.

### <a name="images-and-textures"></a>Imágenes y texturas
 Las imágenes y texturas proporcionan color y detalles visuales en juegos y aplicaciones. En los gráficos 3D, las texturas se presentan en una variedad de formatos, tipos y geometrías para admitir diferentes usos. Por ejemplo, los mapas normales proporcionan valores normales de superficie por píxel para una iluminación más detallada de los modelos 3D, y los mapas de cubo proporcionan textura en todas las direcciones para usos como la conversión sky-boxing, reflejos y asignación de textura esférica. Las texturas pueden proporcionar asignaciones de MIP para admitir la representación eficaz en otros niveles de detalle y pueden admitir otros canales de color y ordenaciones de color. Las texturas se pueden almacenar en una variedad de formatos comprimidos que ocupan menos gráficos de memoria dedicada y ayudan a las GPU a obtener acceso a las texturas de forma más eficaz.

 Puede usar el Editor de imágenes de Visual Studio para trabajar con imágenes y texturas en muchos tipos y formatos comunes.

### <a name="3d-models"></a>Modelos 3D
 Los modelos 3D crean espacio y forma en juegos y aplicaciones. Como mínimo, los modelos codifican la posición de los puntos en el espacio 3D (que se conocen como *vértices*), junto con la indexación de datos para definir líneas o triángulos que representan la forma del modelo. Se pueden asociar datos adicionales con estos vértices (por ejemplo, información del color, vectores normales o atributos específicos de la aplicación). Además, cada modelo puede definir atributos de todo el objeto (por ejemplo, qué sombreador se usa para calcular la apariencia de la superficie del objeto o qué textura se le aplica).

 Puede usar el Editor de modelos de Visual Studio para trabajar con modelos 3D en varios formatos comunes.

### <a name="shaders"></a>Sombreadores
 Los sombreadores son programas pequeños específicos del dominio que se ejecutan en la unidad de procesamiento gráfico (GPU). Los sombreadores determinan cómo se transforman los modelos 3D en formas en pantalla y cómo se colorea cada píxel de esas formas. Al crear un sombreador y aplicarlo a un objeto del juego o la aplicación, puede dar al objeto una apariencia única.

 Puede usar el Diseñador de sombras de Visual Studio, que es una herramienta de diseño de sombreadores basada en gráficos, para crear efectos visuales personalizados sin conocer la programación de HLSL.

> [!NOTE]
> Para más información sobre cómo empezar con la programación de DirectX, vea [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Para obtener más información sobre cómo depurar una aplicación basada en DirectX, vea [Diagnóstico de gráficos (Depurar gráficos de DirectX)](../debugger/graphics/visual-studio-graphics-diagnostics.md).

## <a name="directx-version-compatibility"></a>Compatibilidad de versiones de DirectX
 Visual Studio utiliza DirectX para representar recursos en 2D y 3D. Puede seleccionar el representador de DirectX 11 o el representador de software Windows Advanced Rasterization Platform (WARP). El representador de DirectX 11 proporciona un procesamiento de alto rendimiento y acelerado mediante hardware en GPU de DirectX 11 y DirectX 10. El representador WARP ayuda a asegurarse de que los activos funcionen con una amplia gama de equipos (esto incluye equipos que no tienen hardware gráfico moderno y equipos con hardware gráfico integrado). Para obtener más información sobre WARP, vea [Windows Advanced Rasterization Platform (WARP) guide](http://go.microsoft.com/fwlink/p/?LinkId=224634) [Guía de Windows Advanced Rasterization Platform (WARP)].

## <a name="related-topics"></a>Temas relacionados

|Title|Descripción|
|-----------|-----------------|
|[Trabajar con texturas e imágenes](../designers/working-with-textures-and-images.md)|Describe cómo usar Visual Studio para trabajar con imágenes y texturas.|
|[Trabajar con modelos 3D](../designers/working-with-3-d-models.md)|Describe cómo usar Visual Studio para trabajar con modelos 3D.|
|[Trabajar con sombreadores](../designers/working-with-shaders.md)|Describe cómo usar el Diseñador de sombras de Visual Studio para crear y modificar efectos de sombreador personalizados.|
|[Usar activos 3D en un juego o una aplicación](../designers/using-3-d-assets-in-your-game-or-app.md)|Describe cómo usar activos creados mediante el Editor de imágenes, el Editor de modelos o el Diseñador de sombras en su juego o aplicación.|