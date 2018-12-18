---
title: 'Cómo: Exportar una textura que tiene alfa premultiplicado | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 6
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: a68f6c58ad7e497dfc0e91e92f2cf40e4bd8d992
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49897542"
---
# <a name="how-to-export-a-texture-that-has-premultiplied-alpha"></a>Cómo: Exportar una textura que tiene valores alfa previamente multiplicados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La canalización de contenido de la imagen puede generar texturas de alfa premultiplicado a partir de una imagen de origen. Pueden ser más fáciles de usar y más sólidas que las texturas que no contienen alfa previamente multiplicada.  
  
 Este documento muestra estas actividades:  
  
-   Configurar la imagen de origen para que se procese mediante la canalización de contenido de la imagen.  
  
-   Configurar la canalización de contenido de la imagen para generar valores alfa premultiplicados.  
  
## <a name="premultiplied-alpha"></a>Alfa premultiplicado  
 Alfa premultiplicado proporciona varias ventajas sobre el alfa convencional y no premultiplicado, porque representa mejor la interacción real de la luz con material físico separando la contribución de color de la textura (el color que se agrega a la escena) de la translucidez (la cantidad de color subyacente que permite). Algunas de las ventajas de usar alfa premultiplicado son:  
  
-   La combinación con alfa premultiplicado es una operación asociativa; el resultado de combinar varias texturas translúcidas varias es el mismo, independientemente del orden en que se combinan las texturas.  
  
-   Debido a la naturaleza asociativa de la combinación con alfa premultiplicado, la representación de varias pasadas de objetos translúcidos se simplifica.  
  
-   Mediante el uso de alfa premultiplicado, se puede lograr simultáneamente la combinación aditiva pura (estableciendo alfa en cero) y la combinación lineal interpolada. Por ejemplo, en un sistema de partículas, una partícula de fuego aditivamente mezclada puede convertirse en una partícula de humo translúcido que se mezcla mediante el uso de interpolación lineal. Sin alfa multiplicada previamente, tendría que dibujar las partículas de activación con independencia de las partículas de humo, y modificar el estado de presentación entre las llamadas de dibujo.  
  
-   Las texturas que usan alfa premultiplicado se comprimen con mayor calidad que aquellas que no lo hacen, y no presentan el efecto de bordes descolorido, o "halo", que puede producirse cuando se mezclan texturas que no usan alfa premultiplicado.  
  
#### <a name="to-create-a-texture-that-uses-premultiplied-alpha"></a>Para crear una textura que usa alfa multiplicado previamente  
  
1. Comience con una textura básica. Cargue un archivo de imagen existente o cree uno como se describe en [Cómo: Crear una textura básica](../designers/how-to-create-a-basic-texture.md).  
  
2. Configurar el archivo de textura para que lo procese la canalización de contenido de imagen. En el **Explorador de soluciones**, abra el menú contextual del archivo de textura y seleccione **Propiedades**. En **Propiedades de configuración**, la página **General**, establezca la propiedad **Tipo de elemento** en **Canalización de contenido de la imagen**. Asegúrese de que la propiedad **Contenido** esté establecida en **Sí** y **Excluir de la compilación** esté establecido en **No**, y, después, seleccione el botón **Aplicar**. Aparece la página de propiedades de configuración de **Canalización de contenido de la imagen**.  
  
3. Configure la canalización de contenido de la imagen para generar valores alfa premultiplicados. En **Propiedades de configuración**, **Canalización de contenido de la imagen**, la página **General**, establezca la propiedad de **Convertir en formato alfa premultiplicado** en **Sí (/generatepremultipliedalpha)**.  
  
4. Elija el botón **Aceptar** .  
  
   Al compilar el proyecto, la canalización de contenido de la imagen convierte la imagen de origen desde el formato de trabajo al formato de salida que especificó: Esto incluye la conversión de la imagen en formato alfa premultiplicado, y el resultado se copia en la salida del proyecto directorio.



