---
title: 'Cómo: Crear y modificar niveles de MIP | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 9578fd2bdafeaf8c9a3e9fcd3dd5523b4d8cc7f2
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49184293"
---
# <a name="how-to-create-and-modify-mip-levels"></a>Cómo: Crear y modificar niveles de MIP
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En este documento se muestra cómo usar el **Editor de imágenes** para generar y modificar *niveles de MIP* con nivel de detalle (LoD) del espacio de textura.  
  
## <a name="generating-mip-levels"></a>Generar niveles de MIP  
 La *generación de mapas MIP* es una técnica que se usa para aumentar la velocidad de representación y reducir los artefactos de alias en objetos con textura, para lo que se calculan previamente y se almacenan varias copias de una textura de diferentes tamaños. Cada copia, conocida como nivel de MIP, tiene la mitad del ancho y del alto de la copia anterior. Cuando una textura se representa en la superficie de un objeto, se elige automáticamente el nivel de MIP que se corresponde mejor con el área del espacio de pantalla de la superficie con textura. Esto significa que el hardware gráfico no tiene que filtrar las texturas demasiado grandes para mantener una calidad visual coherente. Aunque el costo de memoria de almacenar los niveles de MIP es aproximadamente un 33 % más alto que el de la textura original por sí sola, las mejoras del rendimiento y de la calidad de imagen lo justifican.  
  
#### <a name="to-generate-mip-levels"></a>Para generar niveles de MIP  
  
1.  Comience con una textura básica, como se describe en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md). Para obtener mejores resultados, especifique una textura que tenga un ancho y un alto que sean la potencia de dos del tamaño, por ejemplo, 256, 512, 1024, etc.  
  
2.  Genere los niveles de MIP. En la barra de herramientas del **modo Editor de imágenes**, elija **Avanzado**, **Herramientas**, **Generar Mips**.  
  
     Observe que los botones para **ir al nivel de MIP siguiente** e **ir al nivel de MIP anterior** aparecen ahora en la barra de herramientas del **modo Editor de imágenes**. Si se muestra la ventana **Propiedades**, observe también que las propiedades de solo lectura **Nivel de Mip** y **Número de niveles de MIP** aparecen ahora en las propiedades de la imagen.  
  
## <a name="modifying-mip-levels"></a>Modificar niveles de MIP  
 Para lograr efectos especiales o aumentar la calidad de la imagen a niveles de detalle específicos, puede modificar cada nivel de MIP individualmente. Por ejemplo, puede asignar a un objeto con textura una apariencia diferente a distancia (cuanto mayor sea la distancia, menores serán los niveles de MIP), o puede asegurarse de que las texturas que contienen texto o símbolos sigan siendo legibles incluso en niveles de MIP más pequeños.  
  
#### <a name="to-modify-an-individual-mip-level"></a>Para modificar un nivel de MIP individual  
  
1.  Seleccione el nivel de MIP que quiere modificar. En la barra de herramientas del **modo Editor de imágenes**, use los botones para **ir al nivel de MIP siguiente** e **ir al nivel de MIP anterior** para moverse entre los niveles.  
  
2.  Una vez que haya seleccionado el nivel de MIP que quiere modificar, puede usar las herramientas de dibujo para modificarlo sin cambiar el contenido de otros niveles de MIP. Las herramientas de dibujo están disponibles en la barra de herramientas del **Editor de imágenes**. Después de seleccionar una herramienta, puede cambiar sus propiedades en la ventana **Propiedades**. Para obtener información sobre las herramientas de dibujo y sus propiedades, vea [Editor de imágenes](../designers/image-editor.md).  
  
> [!NOTE]
>  Si no necesita modificar el contenido de los niveles de MIP individuales (como haría para lograr determinados efectos), se recomienda que genere los mapas MIP desde la textura de origen en tiempo de compilación. Esto ayuda a garantizar que los niveles de MIP permanezcan sincronizados con la textura de origen, ya que las modificaciones realizadas en un nivel de MIP no se propagan automáticamente a otros niveles. Para obtener más información sobre cómo generar mapas MIP en tiempo de compilación, vea [Cómo: Exportar una textura que contiene mapas MIP](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md)



