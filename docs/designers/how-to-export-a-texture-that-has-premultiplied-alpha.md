---
title: 'Cómo: Exportar una textura que tiene valores alfa previamente multiplicados'
ms.date: 11/04/2016
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 91da0e1a08cc75bfce86a5d14985c371e17bcded
ms.sourcegitcommit: 42ea834b446ac65c679fa1043f853bea5f1c9c95
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/19/2018
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Cómo: Exportar una textura que tiene valores alfa previamente multiplicados
La canalización de contenido de la imagen puede generar texturas de alfa premultiplicado a partir de una imagen de origen. Pueden ser más fáciles de usar y más sólidas que las texturas que no contienen alfa previamente multiplicada.

 Este documento muestra estas actividades:

-   Configurar la imagen de origen para que se procese mediante la canalización de contenido de la imagen.

-   Configurar la canalización de contenido de la imagen para generar valores alfa premultiplicados.

## <a name="premultiplied-alpha"></a>Alfa premultiplicado
 Alfa premultiplicado proporciona varias ventajas en comparación con alfa convencional y no premultiplicado, porque representa mejor la interacción real de la luz con material físico separando la contribución de color de la textura (el color que agrega a la escena) de la translucidez (la cantidad de color subyacente que permite). Algunas de las ventajas de usar alfa premultiplicado son:

-   La combinación con alfa premultiplicado es una operación asociativa; el resultado de combinar varias texturas translúcidas varias es el mismo, independientemente del orden en que se combinan las texturas.

-   Debido a la naturaleza asociativa de la combinación con alfa premultiplicado, la representación de varias pasadas de objetos translúcidos se simplifica.

-   Mediante el uso de alfa premultiplicado, se puede lograr simultáneamente la combinación aditiva pura (estableciendo alfa en cero) y la combinación lineal interpolada. Por ejemplo, en un sistema de partículas, una partícula de fuego aditivamente mezclada puede convertirse en una partícula de humo translúcido que se mezcla mediante el uso de interpolación lineal. Sin alfa multiplicada previamente, tendría que dibujar las partículas de activación con independencia de las partículas de humo, y modificar el estado de presentación entre las llamadas de dibujo.

-   Las texturas que usan alfa premultiplicado se comprimen con mayor calidad que aquellas que no lo usan y no presentan el efecto de bordes descoloridos (o de "halo") que puede producirse cuando se mezclan texturas que no usan alfa premultiplicado.

#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Para crear una textura que usa alfa multiplicado previamente

1.  Comience con una textura básica. Cargue un archivo de imagen existente o cree uno como se describe en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md).

2.  Configure el archivo de textura para que sea procesado por la canalización de contenido de imagen. En el **Explorador de soluciones**, abra el menú contextual del archivo de textura y seleccione **Propiedades**. En **Propiedades de configuración**, la página **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**. Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**, y, después, seleccione el botón **Aplicar**. Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.

3.  Configure la canalización de contenido de la imagen para generar valores alfa premultiplicados. En **Propiedades de configuración**, **Canalización de contenido de la imagen**, la página **General**, establezca la propiedad de **Convertir en formato alfa premultiplicado** en **Sí (/generatepremultipliedalpha)**.

4.  Elija el botón **Aceptar** .

 Al compilar el proyecto, la canalización de contenido de la imagen convierte la imagen de origen del formato de trabajo al formato de salida especificado (esto incluye la conversión de la imagen del formato de alfa multiplicado previamente) y el resultado se copia en el directorio de resultados del proyecto.