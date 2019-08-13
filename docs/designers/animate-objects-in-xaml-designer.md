---
title: Animar objetos en el Diseñador XAML
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: fb88fa26-e835-47f5-9771-2f279441c83c
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4b396c0428f9810fe41fa70aca7b52fba2dd4f5b
ms.sourcegitcommit: 90c3187d804ad7544367829d07ed4b47d3f8a72d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/06/2019
ms.locfileid: "68822181"
---
# <a name="animate-objects-in-xaml-designer"></a>Animar objetos en el Diseñador XAML

Blend para Visual Studio le permite crear fácilmente animaciones cortas para el movimiento y el fundido de objetos, por ejemplo.

Para crear una animación, necesita un *guion gráfico*. que puede contener una o más *escalas de tiempo*. Establezca *fotogramas clave* en una escala de tiempo para marcar los cambios de propiedad. Luego, al ejecutar la animación, Blend para Visual Studio interpola los cambios de propiedad durante el período de tiempo designado, lo que produce una transición fluida. Se puede animar cualquier propiedad que pertenezca a un objeto, incluso las propiedades no visuales.

En las imágenes siguientes se muestra un guion gráfico denominado **Storyboard1**. La escala de tiempo contiene fotogramas clave que marcan la posición X e Y de un rectángulo. Cuando se ejecuta esta animación, el rectángulo se mueve de una posición a otra de manera fluida.

![Guion gráfico para animación en Blend para Visual Studio](../designers/media/storyboard-timeline.png)

## <a name="create-an-animation"></a>Creación de una animación

1. Para crear un guion gráfico, seleccione el botón **Opciones de guion gráfico** en la ventana **Objetos y escala de tiempo** y, luego, seleccione **Nuevo**.

   ![Agregar un guion gráfico en Blend para Visual Studio](media/new-storyboard.png)

2. En el cuadro de diálogo **Create Storyboard Resource** (Crear recurso Guion gráfico), escriba un nombre para el guion gráfico.

3. En el panel **Recursos** de la vista Diseño, agregue un rectángulo en la parte inferior izquierda de la página.

   ![Rectángulo en el panel Recursos del Diseñador XAML](media/add-rectangle.PNG)

4. En la ventana **Objetos y escala de tiempo**, mueva el puntero de hora amarillo a **3** segundos.

   ![Indicador de hora en la escala de tiempo](media/timeline-indicator.PNG)

5. En la vista Diseño de la página, arrastre el rectángulo hasta el lado derecho de la página.

6. Presione **Reproducir** para ver que el rectángulo se mueve de izquierda a derecha en la página.

Juegue con otros cambios en el rectángulo en distintos momentos. Por ejemplo, puede cambiar el color de relleno o voltear la orientación en la ventana Propiedades.

## <a name="see-also"></a>Vea también

- [Creación de una interfaz de usuario con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)