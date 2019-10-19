---
title: 'Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: a9ebe7ec-4b6f-4ba2-a79e-80fab3db485b
caps.latest.revision: 6
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a852b0e5ac6c6a677caab97279a0b0cb0299d27f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670630"
---
# <a name="how-to-track-your-code-by-customizing-the-scrollbar"></a>Cómo: Hacer un seguimiento del código personalizando la barra de desplazamiento
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Al trabajar con archivos de código largos, puede ser difícil tenerlo todo en mente. Puede personalizar la barra de desplazamiento de la ventana de código para tener una visión general de lo que sucede en el código.

### <a name="to-show-annotations-on-the-scroll-bar"></a>Para mostrar anotaciones en la barra de desplazamiento

1. Puede configurar la barra de desplazamiento para mostrar cambios en el código, puntos de interrupción, errores y marcadores.

     Abra la página de opciones **barra de desplazamiento** (**herramientas, editor de texto opciones. Todos los idiomas** o un idioma específico, o escriba **barra de desplazamiento** en la ventana Inicio rápido).

2. Seleccione **Mostrar anotaciones en la barra de desplazamiento vertical** y después seleccione las anotaciones que quiere ver. (La opción **Marcas** incluye puntos de interrupción y marcadores).

3. Pruébelo ahora. Abra un archivo de código grande y reemplace algo que aparezca en varios lugares del archivo. La barra de desplazamiento muestra el efecto de los reemplazos, por lo que puede revertir los cambios si ha reemplazado algo que no debería haber reemplazado.

     Este es el aspecto de la barra de desplazamiento tras buscar una cadena. Observe que aparecen todas las instancias de la cadena.

     ![La barra de desplazamiento después de buscar una cadena.](../ide/media/enhancedscrollbarsearch.png "EnhancedScrollbarSearch")

     Aquí se muestra la barra de desplazamiento después de reemplazar todas las instancias de la cadena. Verá inmediatamente que la operación ha provocado algunos problemas.

     ![La barra de desplazamiento después de reemplazar una cadena por errores](../ide/media/enhancedscrollbarreplace.png "EnhancedScrollbarReplace")

### <a name="to-set-the-display-mode-for-the-scroll-bar"></a>Para establecer el modo de presentación de la barra de desplazamiento

1. La barra de desplazamiento tiene dos modos: el modo Barra (el predeterminado) y el modo Mapa. El modo Barra solo muestra indicadores de anotación en la barra de desplazamiento. En el modo Mapa, las líneas de código se representan en la barra de desplazamiento. Puede elegir el ancho y si desea que muestren el código subyacente al situar el puntero sobre ellas. Al hacer clic en una ubicación de la barra de desplazamiento, el cursor se desplaza a esa ubicación del código. Las zonas contraídas están sombreadas de forma diferente; se expanden al hacer doble clic en ellas.

     En la página de opciones **Barra de desplazamiento**, seleccione **Usar el modo Barra para la barra de desplazamiento vertical** o **Usar el modo Mapa para la barra de desplazamiento vertical**. Puede elegir el ancho en la lista desplegable **Información general del código fuente**.

     Este es el aspecto del ejemplo de búsqueda cuando el modo Mapa está activado y el ancho se establece en Medio:

     ![Barra de desplazamiento en modo de mapa](../ide/media/enhancedscrollbar.png "EnhancedScrollbar")

2. En el modo Mapa, a fin de habilitar las vistas previas del código al mover el cursor hacia arriba y hacia abajo por la barra de desplazamiento, seleccione la opción **Mostrar información sobre herramientas de la vista previa**. Este es su aspecto:

     ![La barra de desplazamiento con información sobre herramientas](../ide/media/enhancedscrollbarsearchtooltip.png "EnhancedScrollbarSearchTooltip")

     Si quiere mantener el comportamiento de desplazamiento del modo Mapa y la información sobre herramientas de vista previa pero no quiere ver la información general del código fuente, puede establecer **Información general del código fuente** en **Desactivado**.
