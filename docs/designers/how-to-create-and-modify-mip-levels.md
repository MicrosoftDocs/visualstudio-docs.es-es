---
title: "C&#243;mo: Crear y modificar niveles de MIP | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f64d4369-2307-4175-a39a-2e45506f7fa1
caps.latest.revision: 14
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 14
---
# C&#243;mo: Crear y modificar niveles de MIP
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En este documento se muestra cómo usar el **Editor de imágenes** para generar y modificar *niveles MIP* para el nivel de detalle \(LoD\) del espacio de textura.  
  
## Generar niveles de MIP  
 *Mipmapping* es una técnica que se utiliza para aumentar la velocidad de representación y reducir los artefactos de aliasing en objetos con textura precalculando y almacenando varias copias de una textura en diferentes tamaños.  Cada copia, que se conoce como un nivel de MIP, es la mitad del ancho y del alto de la copia anterior.  Cuando una textura se presenta en la superficie de un objeto, el nivel de MIP que se corresponda más estrechamente con el área de espacio de pantalla de la superficie con textura se elegirá automáticamente.  Esto significa que el hardware gráfico no tiene que filtrar texturas de gran tamaño para mantener una calidad visual coherente.  Aunque el costo de la memoria de almacenar los niveles de MIP es aproximadamente un 33 por ciento más que la textura original sola, las mejoras en el rendimiento y en la calidad de imagen lo justifican.  
  
#### Para generar niveles MIP  
  
1.  Comience con una textura básica, como se describe en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md).  Para obtener los mejores resultados, especifique una textura con un ancho y alto que sean una potencia de dos en tamaño, por ejemplo, 256, 512, 1024 y así sucesivamente.  
  
2.  Genere los niveles de MIP.  En la barra de herramientas del **Modo editor de imágenes**, elija **Avanzadas**, **Herramientas**, **Generar Mips**.  
  
     Observe que los botones **Ir al siguiente nivel de MIP** e **Ir al anterior nivel de MIP** aparecen ahora en la barra de herramientas del **Modo del editor de imágenes**.  Si se muestra la ventana **Propiedades**, observe también que las propiedades de solo lectura **Nivel MIP** y **Número de nivel MIP** aparecen en las propiedades de la imagen.  
  
## Modificar niveles de MIP  
 Para lograr efectos especiales o aumentar la calidad de imagen en niveles de detalle concretos, puede modificar cada nivel MIP por separado.  Por ejemplo, puede asignar a un objeto texturizado un aspecto diferente a una distancia \(una distancia mayor se corresponde con niveles de MIP menores\) o asegurarse de que las texturas que contienen texto o símbolos sigan siendo legibles incluso a niveles de MIP más pequeños.  
  
#### Para modificar un nivel MIP concreto  
  
1.  Seleccione el nivel MIP que desee modificar.  En la barra de herramientas del **Modo editor de imágenes**, use los botones de **Ir al siguiente nivel de MIP** e **Ir al anterior nivel de MIP** para desplazarse entre los niveles de MIP.  
  
2.  Cuando haya seleccionado el nivel de MIP que desea modificar, puede utilizar las herramientas de dibujo disponibles para modificarlo sin cambiar el contenido de otros niveles de MIP.  Las herramientas de dibujo están disponibles en la barra de herramientas del **Editor de imágenes**.  Después de seleccionar una herramienta, puede cambiar sus propiedades en la ventana **Propiedades**.  Para obtener información sobre las herramientas de dibujo y sus propiedades, vea [Editor de imágenes](../designers/image-editor.md).  
  
> [!NOTE]
>  Si no necesita modificar el contenido de niveles de MIP individuales \(como sería conveniente para lograr ciertos efectos\) se recomienda que genere mapas MIP a partir de la textura de origen en tiempo de compilación.  Esto ayuda a garantizar que los niveles de MIPS permanezcan sincronizados con la textura de origen porque las modificaciones a un nivel de MIPS no se propagan a otros niveles automáticamente.  Para obtener más información sobre cómo generar mapas MIP en tiempo de compilación, vea [Cómo: Exportar una textura que contiene mapas MIP](../designers/how-to-export-a-texture-that-contains-mipmaps.md).  
  
## Vea también  
 [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md)