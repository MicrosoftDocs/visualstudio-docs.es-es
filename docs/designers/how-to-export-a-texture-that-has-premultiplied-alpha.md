---
title: "C&#243;mo: Exportar una textura que tiene valores alfa previamente multiplicados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 4
caps.handback.revision: 4
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# C&#243;mo: Exportar una textura que tiene valores alfa previamente multiplicados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La canalización de contenido de la imagen puede generar texturas de alfa premultiplicado a partir de una imagen de origen.  Pueden ser más fáciles de usar y más sólidas que las texturas que no contienen alfa previamente multiplicada.  
  
 En este documento se muestran estas actividades:  
  
-   Configurar la imagen de origen para que se procese mediante Canalización de contenido de la imagen.  
  
-   Configurar Canalización de contenido de la imagen para generar valores alfa premultiplicados.  
  
## Alfa premultiplicado  
 Alfa premultiplicado proporciona varias ventajas en comparación con alfa convencional y no premultiplicado, porque representa mejor la interacción real de la luz con material físico separando la contribución de color de la textura \(el color que agrega a la escena\) de la translucidez \(la cantidad de color subyacente que permite\).  Algunas de las ventajas de utilizar alfa premultiplicada son:  
  
-   La combinación con alfa premultiplicada es una operación asociativa; el resultado de combinar varias texturas translúcidas varias es el mismo, independientemente del orden en que se combinan las texturas.  
  
-   Debido a la naturaleza asociativa de la combinación con alfa premultiplicada, la representación de varias pasadas de objetos translúcidos se simplifica.  
  
-   Mediante el uso de alfa premultiplicada, se puede lograr simultáneamente la combinación aditiva pura \(estableciendo alfa en cero\) y la combinación lineal interpolada.  Por ejemplo, en un sistema de partículas, una partícula de fuego aditivamente mezclada puede convertirse en una partícula de humo translúcido que se mezcla mediante el uso de interpolación lineal.  Sin alfa multiplicada previamente, tendría que dibujar las partículas de activación con independencia de las partículas de humo, y modificar el estado de presentación entre las llamadas de dibujo.  
  
-   Las texturas que usan alfa premultiplicado se comprimen con mayor calidad que aquellas que no lo usan y no presentan el efecto de bordes descoloridos \(o de "halo"\) que puede producirse cuando se mezclan texturas que no utilizan alfa premultiplicado.  
  
#### Para crear una textura que usa alfa multiplicada previamente  
  
1.  Comience con una textura básica.  Cargue un archivo de imagen existente o cree uno como se describe en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md).  
  
2.  Configure el archivo de textura para que sea procesado por la canalización de contenido de imagen.  En **Explorador de soluciones**, abra el menú contextual del archivo de textura y elija **Propiedades**.  En **Propiedades de configuración**, la página **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**.  Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**, y, a continuación, elija el botón **Aplicar**.  Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.  
  
3.  Configure la canalización de contenido de la imagen para generar valores alfa premultiplicados.  En **Propiedades de configuración**, **Canalización de contenido de la imagen**, la página **General**, establezca la propiedad de **convertir en formato alfa premultiplicado** en **Sí \(\/generatepremultipliedalpha\)**.  
  
4.  Elija el botón **Aceptar**.  
  
 Al compilar el proyecto, la Canalización de contenido de la imagen convierte la imagen de origen del formato de trabajo al formato de salida especificado \(esto incluye la conversión de la imagen del formato de alfa multiplicado previamente\) y el resultado se copia en el directorio de resultados del proyecto.