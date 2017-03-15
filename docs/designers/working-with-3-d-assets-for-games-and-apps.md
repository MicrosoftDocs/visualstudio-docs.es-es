---
title: "Trabajar con activos 3D para juegos y aplicaciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.graphics"
ms.assetid: 910d673b-c884-4eeb-9928-0e89f3d38cb6
caps.latest.revision: 24
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 24
---
# Trabajar con activos 3D para juegos y aplicaciones
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se describen las herramientas de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] que puede utilizar para crear o modificar modelos, texturas y sombreadores 3D para juegos y aplicaciones basadas en DirectX.  
  
## Desarrollo de aplicaciones de DirectX en Visual Studio  
 Una aplicación de DirectX combina lógica mediante programación, la API de DirectX y programas de HLSL \(High Level Shading Language\), así como activos visuales 3D y de audio para ofrecer una variada experiencia multimedia interactiva.  [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] incluye herramientas que puede utilizar para trabajar con imágenes y texturas, modelos 3D y sombreadores sin dejar el IDE para utilizar otra herramienta.  Las herramientas de Visual Studio son especialmente indicadas para crear activos de *marcador de posición*, que puede utilizar para probar código o crear prototipos antes de poner en funcionamiento activos listos para producción, y para inspeccionar y modificar activos listos para producción durante la depuración de la aplicación.  
  
 A continuación se ofrece más información sobre las clases de activos con los que se puede trabajar en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
### Imágenes y texturas  
 Las imágenes y las texturas proporcionan el color y el detalle visual en juegos y aplicaciones.  En los gráficos 3D, las texturas se presentan en diversos formatos, tipos y geometrías para admitir usos diferentes.  Por ejemplo, los mapas normales proporcionan normales de superficie para una iluminación más detallada de modelos 3D y los mapas de cubo proporcionan texturas en todas las direcciones para usos como en encuadres con cielos, reflexiones y asignación de texturas esféricas.  Las texturas pueden proporcionar mapas MIP para conseguir una representación eficaz en diferentes niveles de detalle, y pueden admitir varios canales y clasificaciones de color.  Las texturas pueden almacenarse en una variedad de formatos comprimidos que ocupan menos memoria dedicada de gráficos y ayudan a las GPU a tener acceso a las texturas más eficazmente.  
  
 Puede utilizar el Editor de imágenes de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con imágenes y texturas de muchos tipos y formatos comunes.  
  
### Modelos 3D  
 Los modelos 3D crean espacios y formas en juegos y aplicaciones.  Como mínimo, los modelos codifican la posición de los puntos en el espacio 3D, que se conocen como *vértices*, junto con los datos de indización para definir las líneas o triángulos que representan la forma del modelo.  Los datos adicionales se pueden asociar a estos vértices, por el ejemplo, la información de color, los vectores normales o los atributos específicos de la aplicación.  Cada modelo puede definir también atributos de ancho del objeto, por ejemplo, qué sombreador se usa para calcular el aspecto de la superficie del objeto o qué textura se le aplica.  
  
 Puede utilizar el Editor de modelos de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con modelos 3D de varios formatos comunes.  
  
### Sombreadores  
 Los sombreadores son programas pequeños, específicos de un dominio, que se ejecutan en la unidad central \(GPU\) de gráficos.  Los sombreadores determinan cómo se transforman los modelos 3D se transforman en formas en pantalla y cómo se colorea cada píxel de esas formas.  Al crear un sombreador y aplicarlo a un objeto en el juego o aplicación, puede asignar al objeto un aspecto único.  
  
 Puede utilizar el Diseñador de sombras de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], que es una herramienta de diseño de sombreadores basada en gráficos, para crear efectos visuales personalizados sin tener conocimientos de programación de HLSL.  
  
> [!NOTE]
>  Para obtener más información sobre cómo iniciar con DirectX que programa, vea [DirectX](http://go.microsoft.com/fwlink/p/?LinkId=224633).  Para obtener más información sobre cómo depurar una aplicación DirectX\-basada, vea [Diagnóstico de gráficos \(Depurar gráficos de DirectX\)](../debugger/visual-studio-graphics-diagnostics.md).  
  
## Compatibilidad de versiones de DirectX  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utiliza DirectX para generar los 2d y 3D activos.  Puede seleccionar el representador de DirectX 11 o el representador de software de Windows Advanced Rasterization Platform \(WARP\).  El representador de DirectX 11 proporciona una representación de alto rendimiento con aceleración por hardware en las GPU de DirectX 11 y DirectX 10.  El representador WARP ayuda a comprobar que los activos funcionan con una gran variedad de equipos, lo que incluye equipos que no tienen hardware de gráficos moderno y equipos con hardware de gráficos integrado.  Para obtener más información sobre WARP, vea [Windows avanzada de guía de \(WARP\) de plataforma de la rasterización](http://go.microsoft.com/fwlink/p/?LinkId=224634).  
  
## Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Trabajar con texturas e imágenes](../designers/working-with-textures-and-images.md)|Describe cómo usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con imágenes y texturas.|  
|[Trabajar con modelos 3D](../designers/working-with-3-d-models.md)|Describe cómo usar [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para trabajar con modelos 3D.|  
|[Trabajar con sombreadores](../designers/working-with-shaders.md)|Describe cómo usar el diseñador de sombras de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] para crear y modificar efectos personalizados del sombreador.|  
|[Usar activos 3D en un juego o una aplicación](../designers/using-3-d-assets-in-your-game-or-app.md)|Describe cómo usar los activos, que ha creado con el editor de imágenes, editor de modelos o diseñador de sombras en su juego o aplicación.|