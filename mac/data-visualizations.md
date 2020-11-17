---
title: Depuración - Visualizaciones de datos
description: La depuración es una parte común y necesaria de la programación. Visual Studio para Mac contiene un completo conjunto de características para facilitar la depuración. En este artículo se examinan las distintas visualizaciones de datos que se pueden ver al inspeccionar objetos en el depurador.
author: jmatthiesen
ms.author: jomatthi
ms.date: 11/09/2020
ms.technology: vs-ide-debug
ms.assetid: 527E6BEC-EF15-4002-ACB5-62AE1C16F6B7
ms.openlocfilehash: 838762435268ea06c09392475f294dbb22c3038d
ms.sourcegitcommit: 2cf3a03044592367191b836b9d19028768141470
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2020
ms.locfileid: "94493249"
---
# <a name="data-visualizations"></a>Visualizaciones de datos

Visual Studio para Mac incluye compatibilidad de la interfaz de usuario con el depurador, lo que permite visualizar los valores de una variable, un campo o una propiedad durante la depuración. Estos visualizadores de datos muestran una versión extendida de los datos y permiten a los desarrolladores inspeccionar estructuras conocidas, por ejemplo para mostrar el color de una estructura de color.

Los visualizadores de la ventana de depuración **Variables locales** se pueden mostrar al hacer clic en el icono de vista previa que aparece a la derecha del valor cuando el usuario se desplaza sobre la fila:

![Ventana Locales](media/data-visualizations-image9.png)

La siguiente lista contiene muchas de las nuevas visualizaciones disponibles durante la depuración en Visual Studio para Mac.

## <a name="point"></a>Punto
Una propiedad Point/PointF o CGPoint en iOS y Mac se presenta como una tupla que muestra los valores X e Y en las ventanas de depuración:

![Visualización de punto](media/data-visualizations-image10.png)

## <a name="size"></a>Size
Una propiedad Size/SizeF o CGSize en iOS y Mac se presenta como un rectángulo. Se dibuja a escala hasta que una dimensión aumenta más allá de 250 píxeles, momento en que se escala el rectángulo con la mayor dimensión como 250 píxeles:

[Visualización de tamaño](media/data-visualizations-image11.png)

## <a name="rectangle"></a>Rectángulo
Una propiedad Rectangle/RectangleF o CGRect en iOS y Mac muestra las dimensiones y el origen. De forma similar al tamaño, se dibuja a escala, hasta que una dimensión aumenta más allá de 250 píxeles:

![Visualización de rectángulo](media/data-visualizations-image12.png)

## <a name="coordinate"></a>Coordenada
Las coordenadas se trazan en un mapa, con la ubicación anclada en el centro:

[Visualización de coordenada](media/data-visualizations-image13.png)

## <a name="color"></a>Color
Muestra las propiedades UIColor, CGColor y Color, que representan la vista previa del color; los componentes RGBA; los valores de matiz, saturación y claridad; y el valor hexadecimal del color:

![Visualización de color](media/data-visualizations-image14.png)

## <a name="images"></a>Imágenes

Los medios se presentan a escala, hasta una dimensión máxima de 250 píxeles, y se escalan para ajustarse si la imagen supera los 250 píxeles:

![Visualización de imagen](media/data-visualizations-image15.png)

## <a name="bezier-curves"></a>Curvas Bézier

El visualizador muestra un elemento `NSBezierPath`:

![Visualización de curva Bézier](media/data-visualizations-image16.png)

## <a name="string"></a>String

Una cadena de menos de 100 caracteres se muestra entera, sin vista previa. Las cadenas más largas se muestran enteras en la vista previa. Las cadenas se pueden editar, así que el visualizador incluye un botón Editar que permite editar el valor de cadena en la vista previa o en el Editor de valores de cadena, que se muestra a continuación:

![Visualización de cadena](media/data-visualizations-image17.png)

### <a name="small-strings"></a>Cadenas pequeñas:
![Visualización de cadena pequeña](media/data-visualizations-image18.png)]

### <a name="medium-length-strings"></a>Cadenas medianas:
![Visualización de cadena mediana](media/data-visualizations-image19.png)

### <a name="editor"></a>Editor:

![Visualización de editor](media/data-visualizations-image21.png)

## <a name="ienumerable"></a>IEnumerable

IEnumerable enumera todos los valores; los valores individuales se pueden ver al hacer clic en el botón **Mostrar valores**. La opción IEnumerable no muestra los valores de objetos como `Array`, `ArrayList`, `List<>` y `Dictionary<,>`, ya que estos tienen sus propios visualizadores del depurador.

![Visualización de IEnumerable](media/data-visualizations-image22.png)

## <a name="other-visualizers"></a>Otros visualizadores

A continuación se indican otros tipos que también tienen sus propios visualizadores incorporados:

![Otra visualización](media/data-visualizations-image23.png)

* **Elementos primitivos**
  * Muestra el valor sin formato del tipo primitivo.
* **Enum**
  * Muestra el valor del campo sin el calificador de tipo enum.
* **Tuple**
  * Se muestra en el formato (,).
* **Null**
  * Muestra el valor "null".
* **URL**
  * Muestra un hipervínculo interactivo.
* **IntPtr**
  * Muestra una representación hexadecimal de IntPtr.

## <a name="see-also"></a>Consulte también

- [Inspeccionar las variables en las ventanas automático y variables locales (Visual Studio en Windows)](/visualstudio/debugger/autos-and-locals-windows)
- [Ver cadenas en un visualizador de cadenas (Visual Studio en Windows)](/visualstudio/debugger/string-visualizer-dialog-box)