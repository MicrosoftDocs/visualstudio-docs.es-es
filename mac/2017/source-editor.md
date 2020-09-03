---
title: Editor de código fuente
description: Empleo del editor de código fuente de Visual Studio para Mac
author: heiligerdankgesang
ms.author: dominicn
ms.date: 05/06/2018
ms.assetid: A018A314-C1C4-4F36-BCB6-2D434208FCFE
ms.openlocfilehash: 187805767e9f67851975dccf8513c708c4233ccc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74985210"
---
# <a name="source-editor"></a>Editor de código fuente

Un editor de código fuente de confianza es básico para escribir código de forma sucinta y eficaz. Visual Studio para Mac proporciona un sofisticado editor de código fuente que constituye el núcleo de las interacciones con el IDE. El editor de código fuente proporciona las características que se podrían esperar y que se necesitan para trabajar con facilidad: Desde tareas básicas como resaltado de sintaxis, fragmentos de código y plegado de código, a las ventajas de la integración del compilador Roslyn, como completado de código IntelliSense totalmente funcional.

El editor de código fuente de Visual Studio para Mac permite una experiencia sin problemas con el resto de la funcionalidad del IDE, como la depuración, la refactorización y la integración del control de versiones.

En este artículo se presentan algunas de las características clave del editor de código fuente y se explica cómo usar Visual Studio para Mac para ser lo más productivo posible.

## <a name="the-source-editor-experience"></a>Experiencia del editor de código fuente

Ver el código y desplazarse por él de forma eficaz es una parte integral del flujo de trabajo de desarrollo. Cómo decida ver y mantener el código exactamente es una decisión personal, que varía entre desarrolladores y, a menudo, entre proyectos.

Visual Studio para Mac ofrece variedad de eficaces características para que el desarrollo multiplataforma sea lo más accesible y útil posible. En las secciones siguientes se explican algunos de los aspectos destacados.

## <a name="code-folding"></a>Plegado de código

El plegado de código facilita la administración de archivos de código fuente grandes al permitir a los desarrolladores mostrar u ocultar secciones completas de código, como directivas using, código reutilizable y comentarios e instrucciones #region. El plegado de código está desactivado de forma predeterminada en Visual Studio para Mac.

Para activar el plegado de código, vaya a **Visual Studio > Preferencias > Editor de texto > General > Plegado de código**:

![Opciones de plegado de código](media/source-editor-image1.png)

Este menú también incluye la opción de plegar #regions y comentarios de forma predeterminada y de mostrar una sugerencia con nombre en lugar de código.

Para mostrar u ocultar secciones, use el widget de divulgación situado junto al número de línea:

![Visualización u ocultación de secciones del código](media/source-editor-image2.png)

También puede alternar entre la visualización y la ocultación de los plegados mediante el elemento de menú **Vista > Plegado > Alternar plegado / Alternar todos los plegados de código**:

![Elemento de menú de plegado](media/source-editor-image19.png)

Este elemento de menú también puede usarse para habilitar o deshabilitar el plegado de código.

## <a name="white-space"></a>Espacio en blanco

Puede que necesite ver caracteres invisibles del código fuente. Es una manera visible de asegurarse de cumplir los estándares de codificación y de no desperdiciar espacio innecesariamente. También es útil al escribir F#, que depende de líneas con una sangría precisa para evaluar el código.

Para establecer las opciones para mostrar el espacio en blanco, vaya a **Visual Studio > Preferencias > Editor de texto > Marcadores y reglas**. La selección de esta opción permite establecer _cuándo_  se muestran los caracteres invisibles: Nunca, Al seleccionar o Siempre:

![Opciones para mostrar caracteres invisibles](media/source-editor-image3.png)

También hay disponible una opción para mostrar tabulaciones, espacios y finales de línea:

![Muestra de tabulaciones y espacios](media/source-editor-image4.png)

Los caracteres invisibles aparecen como puntos grises, como se muestra en la imagen siguiente:

![espacio en blanco mostrado](media/source-editor-image22.png)

## <a name="ruler"></a>Regla

La regla de columna es útil para determinar longitudes de línea, especialmente cuando se trabaja en un equipo que tiene directrices de longitud de línea. La regla de columna se puede activar o desactivar si se va a **Visual Studio > Preferencias > Editor de texto > Marcadores y reglas** y se activa (o desactiva) **Mostrar regla de columna**, como se muestra en la imagen siguiente:

![Cuadro de diálogo Preferencias con la opción "Mostrar regla de columna" resaltada](media/source-editor-image5.png)

 Se muestra como una línea vertical gris clara en el editor de código fuente.

## <a name="highlight-identifier-references"></a>Resaltar referencias a identificadores

Cuando la opción "Resaltar referencias a identificadores" está activada, puede seleccionar cualquier símbolo del código fuente y el editor de código fuente le proporciona una guía visual a las demás referencias de ese archivo. Para activar esta opción, vaya a **Visual Studio > Preferencias > Editor de texto > Marcadores y reglas** y active _Resaltar referencias a identificadores_, como se muestra en la imagen siguiente:

![Cuadro de diálogo Preferencias con la opción "Resaltar referencias a identificadores" resaltada](media/source-editor-image6.png)

El color del resaltado también resulta útil para indicar que un elemento está asignado o tiene una referencia. Si un elemento está asignado, se resalta en rojo; si tiene una referencia, en azul:

![Ejemplo en el que se muestra el color de resaltado](media/source-editor-image7.png)

## <a name="see-also"></a>Vea también

- [Características del editor de código (Visual Studio en Windows)](/visualstudio/ide/writing-code-in-the-code-and-text-editor)
- [Esquematizar (Visual Studio en Windows)](/visualstudio/ide/outlining)