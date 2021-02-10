---
title: Modo Mapa y modo Barra de la barra de desplazamiento
description: Aprenda a realizar un seguimiento de los cambios en el código mediante la personalización de la barra de desplazamiento, y aprenda también a usar el modo de barra y el modo de mapa.
ms.custom: SEO-VS-2020
ms.date: 03/20/2020
ms.topic: how-to
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 740a1b9385c53c87e8d52d2e80729586557f7ce0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99869159"
---
# <a name="how-to-customize-the-scroll-bar"></a>Procedimiento Personalizar la barra de desplazamiento

Al trabajar con archivos de código largo, puede ser difícil llevar la cuenta de todo lo que está en el archivo. Puede personalizar la barra de desplazamiento del editor de código para tener una visión general de lo que sucede en el código.

## <a name="annotations"></a>Anotaciones

Puede seleccionar si la barra de desplazamiento muestra anotaciones como cambios de código, puntos de interrupción, marcadores, errores y posición del símbolo de intercalación.

   1. Para abrir la página de opciones **Barras de desplazamiento**, elija **Herramientas** > **Opciones** > **Editor de texto** > **Todos los lenguajes** > **Barras de desplazamiento**.

   2. Seleccione **Mostrar anotaciones en la barra de desplazamiento vertical** y seleccione las anotaciones que quiere ver. Las anotaciones disponibles son:

      - cambios
      - marcas
      - errores
      - posición del símbolo de intercalación

      > [!TIP]
      > La opción **Mostrar marcas** incluye puntos de interrupción y marcadores.

Para probarla, abra un archivo de código largo y reemplace texto que aparezca en distintos lugares del archivo. La barra de desplazamiento muestra el efecto de los reemplazos, por lo que puede revertir los cambios si ha reemplazado algo que no debería haber reemplazado.

Este es el aspecto de la barra de desplazamiento tras buscar una cadena. Observe que todas las instancias de la cadena aparecen en la barra de desplazamiento.

![Barra de desplazamiento de Visual Studio después de buscar una cadena](../ide/media/enhancedscrollbarsearch.png)

Aquí se muestra la barra de desplazamiento después de reemplazar todas las instancias de la cadena. Las marcas rojas en la barra de desplazamiento muestran dónde el reemplazo de texto generó errores.

![Barra de desplazamiento de Visual Studio después de reemplazar una cadena con errores](../ide/media/enhancedscrollbarreplace.png)

## <a name="display-modes"></a>Modos de presentación

La barra de desplazamiento tiene dos modos: el modo Barra y el modo Mapa.

### <a name="bar-mode"></a>Modo Barra

El *modo Barra* muestra indicadores de anotación en la barra de desplazamiento. Al hacer clic en la barra de desplazamiento, se desplaza hacia arriba o hacia abajo de la página pero no salta a esa ubicación en el archivo.

### <a name="map-mode"></a>Modo Mapa

El *modo Mapa* muestra líneas de código en miniatura en la barra de desplazamiento. Puede elegir el ancho de la columna del mapa si selecciona un valor en **Información general del código fuente**. Para habilitar una vista previa más grande del código cuando deja el puntero en el mapa, seleccione la opción **Mostrar información sobre herramientas de la vista previa**. Las zonas contraídas están sombreadas de manera diferente y se expanden cuando se hace doble clic en ellas.

> [!TIP]
> Para desactivar la vista de código en miniatura en el mapa, establezca **Información general del código fuente** en **Off**. Si se selecciona **Mostrar información sobre herramientas de la vista previa**, seguirá viendo una vista previa del código en esa ubicación cuando mantenga el puntero del mouse sobre la barra de desplazamiento y el cursos seguirá saltando a esa ubicación en el archivo cuando se haga clic.

En la imagen siguiente se muestra el ejemplo de búsqueda cuando el modo Mapa está activo y el ancho está establecido en **Medium** (Mediano):

![Barra de desplazamiento de Visual Studio en el modo Mapa](../ide/media/enhancedscrollbar.png)

En la imagen siguiente se muestra la opción **Mostrar información sobre herramientas de la vista previa**:

![Barra de desplazamiento de Visual Studio con información sobre herramientas](../ide/media/enhancedscrollbarsearchtooltip.png)

> [!TIP]
> Para cambiar los colores que se ven en el modo mapa, elija **Herramientas** > **Opciones** > **Entorno** > **Fuentes y colores**. Después, en **Mostrar los elementos**, elija cualquiera de los elementos precedidos por "Información general", realice los cambios de color que quiera y, luego, elija **Aceptar**.

## <a name="see-also"></a>Vea también

- [Características del editor de código](../ide/writing-code-in-the-code-and-text-editor.md)
