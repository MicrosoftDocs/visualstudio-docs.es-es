---
title: Dibujar formas y trazados
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 97172253a088be86f20fae77fe62d01330a3b801
ms.sourcegitcommit: 206e738fc45ff8ec4ddac2dd484e5be37192cfbd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/03/2018
ms.locfileid: "39513103"
---
# <a name="draw-shapes-and-paths"></a>Dibujar formas y trazados

En el Diseñador XAML, una *forma* es exactamente lo que esperaría. por ejemplo: un rectángulo, un círculo o una elipse. Un *trazado* es una versión más flexible de una forma Puede cambiar su apariencia o combinarlos para crear formas nuevas.

Las formas y los trazados usan gráficos vectoriales, por lo que se adaptan bien a pantallas de alta resolución. Si quiere obtener más información sobre los gráficos vectoriales, consulte [What are Vector Graphics](https://www.youtube.com/watch?v=MoCSwF0n-io) (¿Qué son los gráficos vectoriales) o [vector graphics](http://www.webopedia.com/TERM/V/vector_graphics.html)(Gráficos vectoriales).

##  <a name="Shape"></a> Dibujar una forma
 Las formas se encuentran en el panel **Activos** .

 ![Categoría Formas en el panel Activos](../designers/media/b4_shapes_assetspanel.png)

 Arrastre la forma que desee a la mesa de trabajo. Después puede utilizar los controladores de la forma para escalar, girar, mover o sesgar la forma.

 ![Handles](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

##  <a name="Path"></a> Dibujar un trazado
 Un trazado se compone de varias líneas y curvas conectadas. Utilice un trazado para crear formas interesantes que no están disponibles en el panel **Activos** .

 Los trazados se pueden dibujar con una línea, una pluma o un lápiz, herramientas que se encuentran en el panel **Herramientas** .

 ![Herramienta lápiz](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png) ![Opciones de la herramienta Lápiz](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png)

### <a name="draw-a-straight-line"></a>Dibujar una línea recta
 Use la herramienta **Lápiz** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) o la herramienta **Línea** ![Herramienta Línea](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png).

 **Uso de la herramienta Lápiz** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png)

 En la mesa de trabajo, haga clic una vez para definir el punto inicial y vuelva a hacer clic para definir el final de la línea.

 **Uso de la herramienta Línea** ![Herramienta Línea](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png)

 En la mesa de trabajo, arrastre desde el punto en el que desea que empiece la línea y después suelte en el punto en el que desea que finalice.

### <a name="draw-a-curve"></a>Dibujar una curva
 Use la herramienta **Lápiz** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 En la mesa de trabajo, haga clic una vez para definir el punto inicial de una línea y, a continuación, haga clic y arrastre el puntero para crear la curva deseada.

 Si desea cerrar el trazado, haga clic en el primer punto en la línea.

### <a name="change-the-shape-of-a-curve"></a>Cambiar la forma de una curva
 Use la herramienta **Selección directa** ![Herramienta Selección directa](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Haga clic en la forma y después arrastre cualquier punto de la forma para cambiar la curva.

### <a name="draw-a-free-form-path"></a>Dibujar un trazado de forma libre
 Use la herramienta **Lápiz** ![Herramienta Lápiz](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png).

 En la mesa de trabajo, dibuje un trazado de forma libre como si estuviera usando un lápiz real.

### <a name="remove-part-of-a-path"></a>Quitar parte de un trazado
 Use la herramienta **Selección directa** ![Herramienta Selección directa](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png).

 Seleccione el trazado que contiene el segmento que desea eliminar y después haga clic en el botón **Eliminar** .

### <a name="remove-a-point-in-a-path"></a>Quitar un punto de un trazado
 Use la herramienta **Selección** ![Herramienta Selección](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) y la herramienta **Lápiz** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Use la herramienta **Selección** ![Herramienta Selección](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) para seleccionar el trazado. Después, use la herramienta **Lápiz** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) para hacer clic en el punto que quiera quitar.

### <a name="add-a-point-to-a-path"></a>Agregar un punto en un trazado
 Use la herramienta **Selección** ![Herramienta Selección](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) y la herramienta **Lápiz** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png).

 Use la herramienta **Selección** ![Herramienta Selección](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png) para seleccionar el trazado. Use la herramienta **Pluma** ![Herramienta Lápiz](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png) para hacer clic en cualquier lugar del trazado en el que quiera agregar el punto.

##  <a name="Convert"></a> Convertir una forma en un trazado
 Para modificar una forma de la misma forma que se modifica un trazado, convierta la forma en un trazado.

 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: convertir una forma en un trazado](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

##  <a name="Combine"></a> Combinar trazados
 Los trazados y las formas se pueden combinar en un único trazado.

 ![Combinar trazados](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|||||
|-|-|-|-|
|![Dos formas antes de su combinación](../designers/media/b1_1.png)|Dos formas antes de su combinación|![Formar intersección](../designers/media/b1_4.png)|Formar intersección|
|![Excluir superposición](../designers/media/b1_2.png)|Unir|![](../designers/media/b1_5.png)|Excluir superposición|
|![Restar](../designers/media/b1_3.png)|Dividir|![](../designers/media/b1_6.png)|Restar|

 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: combinar trazados](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

##  <a name="Compound"></a> Crear un trazado compuesto
 Cuando se crea un trazado compuesto, las partes en intersección de los trazados se restan del resultado final y el trazado resultante adopta las propiedades visuales del trazado situado al fondo.

 Una vez creados, los trazados compuestos se pueden separar en cualquier momento.

 ![Crear un trazado compuesto](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: crear un trazado compuesto](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

##  <a name="Clipping"></a> Crear un trazado de recorte
 Un trazado de recorte es un trazado o forma que se aplica a otro objeto, ocultando así las partes del objeto con máscara que sobresalen del trazado de recorte.

 ![Trazado de recorte](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: crear un trazado de recorte](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).

## <a name="see-also"></a>Vea también

- [Crear una IU con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)