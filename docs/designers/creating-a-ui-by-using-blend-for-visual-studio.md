---
title: Paseo por las características de Blend para Visual Studio
titleSuffix: ''
ms.date: 07/31/2019
ms.topic: conceptual
f1_keywords:
- Blend.Start.Dev12
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e204e3a51608b078f1220fe9050eea5be12241cb
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822240"
---
# <a name="blend-for-visual-studio-overview"></a>Introducción de Blend para Visual Studio

Blend para Visual Studio le ayuda a diseñar aplicaciones web y de Windows basadas en XAML. Proporciona la misma experiencia de diseño XAML básica que Visual Studio y agrega diseñadores visuales para tareas avanzadas como animaciones y comportamientos. Para ver una comparación entre Blend y Visual Studio, vea [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md).

Blend para Visual Studio es un componente de Visual Studio. Para instalar Blend, en el **instalador de Visual Studio** elija la carga de trabajo **Desarrollo de la plataforma universal de Windows** o **Desarrollo de escritorio de .NET**. Ambas cargas de trabajo incluyen el componente Blend para Visual Studio.

![Componentes de carga de trabajo de UWP](media/installer-uwp.png)&nbsp;&nbsp;&nbsp;&nbsp;![Componentes de carga de trabajo de desarrollo de escritorio de .NET](media/installer-dotnet-desktop.png)

Si no ha trabajado nunca con Blend para Visual Studio, tómese un momento para familiarizarse con las características exclusivas del área de trabajo. Este tema le servirá de paseo introductorio.

## <a name="tools-panel"></a>Panel Herramientas

Puede usar el panel **Herramientas** en Blend para Visual Studio para crear y modificar objetos en la aplicación. El panel **Herramientas** aparece a la izquierda del Diseñador XAML cuando se tiene un archivo *.xaml* abierto.

Para crear objetos, seleccione una herramienta y dibuje en la mesa de trabajo utilizando el mouse.

![Panel Herramientas en Blend para Visual Studio](../designers/media/blend-tools-panel.png)

> [!TIP]
> Algunas de las herramientas del panel **Herramientas** tienen variaciones. Por ejemplo, en lugar de un rectángulo, puede elegir una elipse o una línea. Para obtener acceso a estas variantes, haga clic con el botón derecho o haga clic y mantenga presionado el botón en la herramienta.
>
> ![Variantes de la herramienta Forma en Blend para Visual Studio](media/blend-rectangle-tool-variations.png)

### <a name="selection-tools"></a>Herramientas de selección

Seleccione objetos y trazados. Use la herramienta **Selección directa** para seleccionar objetos anidados y segmentos de trazados.

### <a name="view-tools"></a>Herramientas de vista

Ajuste la vista de la mesa de trabajo, por ejemplo para movimiento panorámico y zoom.

### <a name="brush-tools"></a>Herramientas de pincel

Trabaje con los atributos visuales de un objeto, como la transformación de un pincel o la aplicación de un degradado.

### <a name="object-tools"></a>Herramientas de objeto

Dibuje en la mesa de trabajo los objetos más habituales, como trazados, formas, paneles de diseño, texto y controles.

### <a name="asset-tools"></a>Herramientas de recursos

Acceda a la ventana Recursos y muestre el recurso usado más recientemente de la biblioteca.

## <a name="assets-window"></a>Ventana Activos

La ventana **Activos** contiene todos los objetos visuales disponibles y es similar al **cuadro de herramientas** de Visual Studio. Además de los objetos visuales, encontrará todo lo que puede agregar a la mesa de trabajo en la ventana **Activos**, como, por ejemplo, estilos, elementos multimedia, comportamientos y efectos. Para abrir la ventana **Activos**, elija **Ver** > **Ventana Activos** o presione **Ctrl**+**Alt**+**X**.

![Ventana Activos en Blend para Visual Studio](../designers/media/blend-assets-window.png)

- Escriba texto en el cuadro **Buscar recursos** para filtrar la lista de recursos.
- Cambie entre el modo de cuadrícula y el modo de lista para ver los recursos mediante los botones que aparece en la parte superior derecha.

## <a name="objects-and-timeline-window"></a>Ventana Objetos y escala de tiempo

Utilice esta ventana para organizar los objetos en la mesa de trabajo y, si quiere, para animarlos. Para abrir la ventana **Objetos y escala de tiempo**, elija **Ver** > **Esquema del documento**. Además de la funcionalidad proporcionada en la [ventana Esquema del documento](creating-a-ui-by-using-xaml-designer-in-visual-studio.md#document-outline-window) en Visual Studio, la ventana Objetos y escala de tiempo de Blend para Visual Studio tiene un área de composición de la escala de tiempo a la derecha. Use la escala de tiempo al crear y editar animaciones.

![Ventana Objetos y escala de tiempo en modo de animación](../designers/media/storyboard-timeline.png)

Use los botones de guion gráfico ![Botones de guion gráfico de Blend para Visual Studio](media/storyboard-buttons.png) para crear, eliminar, cerrar o seleccionar un guion gráfico. Use el área de composición de la escala de tiempo que se encuentra a la derecha para ver la escala de tiempo y mover fotogramas clave.

Mantenga el puntero sobre cada botón de la ventana para obtener más información sobre la funcionalidad disponible.

## <a name="see-also"></a>Vea también

- [Animar objetos](../designers/animate-objects-in-xaml-designer.md)
- [Dibujar formas y trazados](../designers/draw-shapes-and-paths.md)
- [Diseño de XAML en Visual Studio y Blend para Visual Studio](../designers/designing-xaml-in-visual-studio.md)
