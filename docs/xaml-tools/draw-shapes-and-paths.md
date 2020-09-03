---
title: Dibujar formas y trazados
titleSuffix: Blend for Visual Studio
ms.date: 07/31/2019
ms.topic: conceptual
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b87ed03c8f513f6a9a750186d8763e56061bed98
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "85350828"
---
# <a name="draw-shapes-and-paths"></a>Dibujar formas y trazados

En Diseñador XAML, una *forma* es exactamente lo que cabría esperar. por ejemplo: un rectángulo, un círculo o una elipse. Un *trazado* es una versión más flexible de una forma Puede cambiar su apariencia o combinarlos para crear formas nuevas.

Las formas y los trazados usan gráficos vectoriales, por lo que se adaptan bien a pantallas de alta resolución.

## <a name="draw-a-shape"></a>Dibujar una forma

Busque formas en la ventana **Recursos**.

![Categoría Formas en la ventana Recursos](media/blend-shapes.png)

Arrastre la forma que desee a la mesa de trabajo. Después, use los controladores de la forma para escalar, girar, mover o sesgar la forma.

![Asas](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png)

## <a name="draw-a-path"></a>Dibujar un trazado

Un trazado se compone de varias líneas y curvas conectadas. Use un trazado para crear formas interesantes que no están disponibles en la ventana **Recursos**.

Los trazados se pueden dibujar con una línea, una pluma o un lápiz, Puede encontrar estas herramientas en la ventana **Herramientas**.

### <a name="draw-a-straight-line"></a>Dibujar una línea recta

Use la herramienta **Pluma** o la herramienta **Línea**.

**Uso de la herramienta Pluma**

En la mesa de trabajo, haga clic una vez para definir el punto inicial y vuelva a hacer clic para definir el final de la línea.

**Uso de la herramienta Línea**

En la mesa de trabajo, arrastre desde el punto en el que desea que empiece la línea y después suelte en el punto en el que desea que finalice.

### <a name="draw-a-curve"></a>Dibujar una curva

Use la herramienta **Pluma**.

En la mesa de trabajo, haga clic una vez para definir el punto inicial de una línea y, a continuación, haga clic y arrastre el puntero para crear la curva deseada.

Si desea cerrar el trazado, haga clic en el primer punto en la línea.

### <a name="change-the-shape-of-a-curve"></a>Cambiar la forma de una curva

Use la herramienta **Selección directa**.

Haga clic en la forma y después arrastre cualquier punto de la forma para cambiar la curva.

### <a name="draw-a-free-form-path"></a>Dibujar un trazado de forma libre

Use la herramienta **Lápiz**.

En la mesa de trabajo, dibuje un trazado de forma libre como si estuviera usando un lápiz real.

### <a name="remove-part-of-a-path"></a>Quitar parte de un trazado

Use la herramienta **Selección directa**.

Seleccione el trazado que contiene el segmento que desea eliminar y después haga clic en el botón **Eliminar** .

### <a name="remove-a-point-in-a-path"></a>Quitar un punto de un trazado

Use la herramienta **Selección** para seleccionar el trazado. A continuación, use la herramienta **Pluma** para hacer clic en el punto que desea quitar.

### <a name="add-a-point-to-a-path"></a>Agregar un punto en un trazado

Use la herramienta **Selección** para seleccionar el trazado. Use la herramienta **Pluma** para hacer clic en cualquier lugar del trazado en el que desee agregar el punto.

## <a name="convert-a-shape-to-a-path"></a>Convertir una forma en un trazado

Para modificar una forma de la misma forma que se modifica un trazado, convierta la forma en un trazado. Seleccione la forma y, a continuación, seleccione **Format**  >  **path**  >  **convertir en trazado**.

**Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: convertir una forma en un trazado](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).

> [!NOTE]
> Actualmente, **Convertir en trazado** no está disponible para las aplicaciones de UWP con una `TargetPlatformVersion` de 10.0.16299.0 o posterior, como mínimo.

## <a name="combine-paths"></a>Combinar trazados

Los trazados y las formas se pueden combinar en un único trazado.

![Combinar trazados](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png)

|Number|Acción|
|-|-|
|![Dos formas antes de su combinación](../designers/media/b1_1.png)|Dos formas antes de su combinación|
|![Unir](../designers/media/b1_2.png)|Unir|
|![Dividir](../designers/media/b1_3.png)|Dividir|
|![Formar intersección](../designers/media/b1_4.png)|Formar intersección|
|![Excluir superposición](../designers/media/b1_5.png)|Excluir superposición|
|![Restar](../designers/media/b1_6.png)|Restar|

**Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: combinar trazados](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).

## <a name="create-a-compound-path"></a>Crear un trazado compuesto

Cuando se crea un trazado compuesto, las partes en intersección de los trazados se restan del resultado final y el trazado resultante adopta las propiedades visuales del trazado situado al fondo.

Una vez creados, los trazados compuestos se pueden separar en cualquier momento.

![Crear un trazado compuesto](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png)

**Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: crear un trazado compuesto](https://www.youtube.com/watch?v=Io5bC0-nH6Q).

## <a name="create-a-clipping-path"></a>Crear un trazado de recorte

Un trazado de recorte es un trazado o forma que se aplica a otro objeto, ocultando así las partes del objeto con máscara que sobresalen del trazado de recorte.

![Trazado de recorte](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png)

**Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png) [Trabajar con trazados: crear un trazado de recorte](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).
