---
title: Trabajar con activos 3D para juegos y aplicaciones | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.graphics
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: "24"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: a4b0cc6e7105f91a4192d2c079854c8953736eaf
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-3-d-assets-for-games-and-apps"></a>Trabajar con activos 3D para juegos y aplicaciones
En este documento, se describen las herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que puede usar para crear o modificar modelos 3D, texturas y sombreadores para aplicaciones y juegos basados en DirectX.  
  
## <a name="directx-app-development-in-visual-studio"></a>Desarrollo de aplicaciones de DirectX en Visual Studio  
 Normalmente, una aplicación de DirectX combina lógica de programación, la API de DirectX y programas de lenguaje de sombreado de alto nivel (HLSL), junto con activos visuales 3D y de audio para presentar una experiencia multimedia enriquecida e interactiva.[!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incluye herramientas para trabajar con imágenes y texturas, modelos 3D y sombreadores sin salir del IDE para usar otra herramienta. Las herramientas de Visual Studio son especialmente adecuadas para crear activos de *marcador de posición*, que sirven para probar el código o compilar prototipos antes de programar activos listos para producción, y para inspeccionar y modificar activos listos para producción cuando depura la aplicación.  
  
 Aquí tiene más información sobre los tipos de activos con los que puede trabajar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### <a name="images-and-textures"></a>Imágenes y texturas  
 Las imágenes y texturas proporcionan color y detalles visuales en juegos y aplicaciones. En los gráficos 3D, las texturas se presentan en una variedad de formatos, tipos y geometrías para admitir diferentes usos. Por ejemplo, los mapas normales proporcionan valores normales de superficie por píxel para una iluminación más detallada de los modelos 3D, y los mapas de cubo proporcionan textura en todas las direcciones para usos como la conversión sky-boxing, reflejos y asignación de textura esférica. Las texturas pueden proporcionar asignaciones de MIP para admitir la representación eficaz en diferentes niveles de detalle y pueden admitir diferentes canales de color y ordenaciones de color. Las texturas se pueden almacenar en una variedad de formatos comprimidos que ocupan menos gráficos de memoria dedicada y ayudan a las GPU a obtener acceso a las texturas de forma más eficaz.  
  
 Puede usar el Editor de imágenes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con imágenes y texturas en muchos tipos y formatos comunes.  
  
### <a name="3-d-models"></a>modelos 3D  
 Los modelos 3D crean espacio y forma en juegos y aplicaciones. Como mínimo, los modelos codifican la posición de los puntos en el espacio 3D (que se conocen como *vértices*), junto con la indexación de datos para definir líneas o triángulos que representan la forma del modelo. Se pueden asociar datos adicionales con estos vértices (por ejemplo, información del color, vectores normales o atributos específicos de la aplicación). Además, cada modelo puede definir atributos de todo el objeto (por ejemplo, qué sombreador se usa para calcular la apariencia de la superficie del objeto o qué textura se le aplica).  
  
 Puede usar el Editor de modelos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con modelos 3D en varios formatos comunes.  
  
### <a name="shaders"></a>Sombreadores  
 Los sombreadores son programas pequeños específicos del dominio que se ejecutan en la unidad de procesamiento gráfico (GPU). Los sombreadores determinan cómo se transforman los modelos 3D en formas en pantalla y cómo se colorea cada píxel de esas formas. Al crear un sombreador y aplicarlo a un objeto del juego o la aplicación, puede dar al objeto una apariencia única.  
  
 Puede usar el Diseñador de sombras de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], que es una herramienta de diseño de sombreadores basada en gráficos, para crear efectos visuales personalizados sin conocer la programación de HLSL.  
  
> [!NOTE]
>  Para más información sobre cómo empezar con la programación de DirectX, vea [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633). Para más información sobre cómo depurar una aplicación basada en DirectX, vea [Graphics Diagnostics (Debugging DirectX Graphics)](../debugger/visual-studio-graphics-diagnostics.md) [Diagnóstico de gráficos (depurar gráficos de DirectX)].  
  
## <a name="directx-version-compatibility"></a>Compatibilidad de versiones de DirectX  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] usa DirectX para representar activos 2D y 3D. Puede seleccionar el representador de DirectX 11 o el representador de software Windows Advanced Rasterization Platform (WARP). El representador de DirectX 11 proporciona un procesamiento de alto rendimiento y acelerado mediante hardware en GPU de DirectX 11 y DirectX 10. El representador WARP ayuda a asegurarse de que los activos funcionen con una amplia gama de equipos (esto incluye equipos que no tienen hardware gráfico moderno y equipos con hardware gráfico integrado). Para más información sobre WARP, vea [Windows Advanced Rasterization Platform (WARP) Guide](http://go.microsoft.com/fwlink/p/?LinkId=224634) [Guía de Windows Advanced Rasterization Platform (WARP)].  
  
## <a name="related-topics"></a>Temas relacionados  
  
|Title|Description|  
|-----------|-----------------|  
|[Trabajar con texturas e imágenes](../designers/working-with-textures-and-images.md)|Describe cómo usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con imágenes y texturas.|  
|[Trabajar con modelos 3D](../designers/working-with-3-d-models.md)|Describe cómo usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con modelos 3D.|  
|[Trabajar con sombreadores](../designers/working-with-shaders.md)|Describe cómo usar el Diseñador de sombras de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear y modificar efectos de sombreador personalizados.|  
|[Usar activos 3D en un juego o una aplicación](../designers/using-3-d-assets-in-your-game-or-app.md)|Describe cómo usar activos creados mediante el Editor de imágenes, el Editor de modelos o el Diseñador de sombras en su juego o aplicación.|