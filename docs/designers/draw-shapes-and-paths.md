---
title: "Dibujar formas y trazados | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d5378c59-e2e5-49f0-91f1-aa82d984a33c
caps.latest.revision: 10
caps.handback.revision: 10
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Dibujar formas y trazados
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

En el Diseñador XAML, una *forma* es exactamente lo que cabría esperar, por ejemplo: un rectángulo, un círculo o una elipse. Un *trazado* es una versión más flexible de una forma Puede cambiar su apariencia o combinarlos para crear formas nuevas.  
  
 Las formas y los trazados usan gráficos vectoriales, por lo que se adaptan bien a pantallas de alta resolución. Si quiere obtener más información sobre los gráficos vectoriales, consulte [What are Vector Graphics](https://www.youtube.com/watch?v=MoCSwF0n-io) \(¿Qué son los gráficos vectoriales\) o [vector graphics](http://www.webopedia.com/TERM/V/vector_graphics.html) \(Gráficos vectoriales\).  
  
 **En este tema:**  
  
-   [Dibujar una forma](#Shape)  
  
-   [Dibujar un trazado](#Path)  
  
-   [Convertir una forma en un trazado](#Convert)  
  
-   [Combinar trazados](#Combine)  
  
-   [Crear un trazado compuesto](#Compound)  
  
-   [Crear un trazado de recorte](#Clipping)  
  
##  <a name="Shape"></a> Dibujar una forma  
 Las formas se encuentran en el panel **Activos**.  
  
 ![Categoría Formas en el panel Activos](../designers/media/b4_shapes_assetspanel.png "b4\_Shapes\_AssetsPanel")  
  
 Arrastre la forma que desee a la mesa de trabajo. Después puede utilizar los controladores de la forma para escalar, girar, mover o sesgar la forma.  
  
 ![](../designers/media/84261e83-3091-4490-ab58-4218b188439e.png "84261e83\-3091\-4490\-ab58\-4218b188439e")  
  
##  <a name="Path"></a> Dibujar un trazado  
 Un trazado se compone de varias líneas y curvas conectadas. Utilice un trazado para crear formas interesantes que no están disponibles en el panel **Activos**.  
  
 Los trazados se pueden dibujar con una línea, una pluma o un lápiz, herramientas que se encuentran en el panel **Herramientas**.  
  
 ![](../designers/media/717956a8-b6a5-4e37-8af3-70bcfc78c82a.png "717956a8\-b6a5\-4e37\-8af3\-70bcfc78c82a") ![](../designers/media/8fbbbb21-be83-4cf6-903b-3a49f00c9860.png "8fbbbb21\-be83\-4cf6\-903b\-3a49f00c9860")  
  
### Dibujar una línea recta  
 Use la herramienta **Pluma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54") o la herramienta **Línea**![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397\-5283\-48be\-8396\-3449be7b6fbf").  
  
 **Uso de la herramienta Pluma** ![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54")  
  
 En la mesa de trabajo, haga clic una vez para definir el punto inicial y vuelva a hacer clic para definir el final de la línea.  
  
 **Uso de la herramienta Línea** ![](../designers/media/eb618397-5283-48be-8396-3449be7b6fbf.png "eb618397\-5283\-48be\-8396\-3449be7b6fbf")  
  
 En la mesa de trabajo, arrastre desde el punto en el que desea que empiece la línea y después suelte en el punto en el que desea que finalice.  
  
### Dibujar una curva  
 Use la herramienta **Pluma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54").  
  
 En la mesa de trabajo, haga clic una vez para definir el punto inicial de una línea y, a continuación, haga clic y arrastre el puntero para crear la curva deseada.  
  
 Si desea cerrar el trazado, haga clic en el primer punto en la línea.  
  
### Cambiar la forma de una curva  
 Use la herramienta **Selección directa**![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f\-c116\-451d\-8dd2\-1f88b8406362").  
  
 Haga clic en la forma y después arrastre cualquier punto de la forma para cambiar la curva.  
  
### Dibujar un trazado de forma libre  
 Use la herramienta **Lápiz**![](../designers/media/509dc167-734f-46c9-b012-987ee63450cd.png "509dc167\-734f\-46c9\-b012\-987ee63450cd").  
  
 En la mesa de trabajo, dibuje un trazado de forma libre como si estuviera usando un lápiz real.  
  
### Quitar parte de un trazado  
 Use la herramienta **Selección directa**![](../designers/media/6dd6571f-c116-451d-8dd2-1f88b8406362.png "6dd6571f\-c116\-451d\-8dd2\-1f88b8406362").  
  
 Seleccione el trazado que contiene el segmento que desea eliminar y después haga clic en el botón **Eliminar**.  
  
### Quitar un punto de un trazado  
 Use la herramienta **Selección**![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa") y la herramienta **Pluma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54").  
  
 Use la herramienta **Selección**![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa") para seleccionar el trazado. A continuación, use la herramienta **Pluma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54") para hacer clic en el punto que desea quitar.  
  
### Agregar un punto en un trazado  
 Use la herramienta **Selección**![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa") y la herramienta **Pluma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54").  
  
 Use la herramienta **Selección**![](../designers/media/2ff91340-477e-4efa-a0f7-af20851e4daa.png "2ff91340\-477e\-4efa\-a0f7\-af20851e4daa") para seleccionar el trazado. Use la herramienta **Pluma**![](../designers/media/894f8612-e0ed-4e00-84cf-a9bc8f38fc54.png "894f8612\-e0ed\-4e00\-84cf\-a9bc8f38fc54") para hacer clic en cualquier lugar del trazado en el que desee agregar el punto.  
  
##  <a name="Convert"></a> Convertir una forma en un trazado  
 Para modificar una forma de la misma forma que se modifica un trazado, convierta la forma en un trazado.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabajar con trazados: convertir una forma en un trazado](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=147).  
  
##  <a name="Combine"></a> Combinar trazados  
 Los trazados y las formas se pueden combinar en un único trazado.  
  
 ![](../designers/media/2df17a5d-a338-4ef4-96c5-dae51cc1ca8a.png "2df17a5d\-a338\-4ef4\-96c5\-dae51cc1ca8a")  
  
|||||  
|-|-|-|-|  
|![](../designers/media/b1_1.png "B1\_1")|Dos formas antes de su combinación|![](../designers/media/b1_4.png "B1\_4")|Formar intersección|  
|![](../designers/media/b1_2.png "B1\_2")|Unir|![](../designers/media/b1_5.png "B1\_5")|Excluir superposición|  
|![](../designers/media/b1_3.png "B1\_3")|Dividir|![](../designers/media/b1_6.png "B1\_6")|Restar|  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabajar con trazados: combinar trazados](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=195).  
  
##  <a name="Compound"></a> Crear un trazado compuesto  
 Cuando se crea un trazado compuesto, las partes en intersección de los trazados se restan del resultado final y el trazado resultante adopta las propiedades visuales del trazado situado al fondo.  
  
 Una vez creados, los trazados compuestos se pueden separar en cualquier momento.  
  
 ![](../designers/media/2157a8aa-d9a7-4de4-8de5-b10d28f08a84.png "2157a8aa\-d9a7\-4de4\-8de5\-b10d28f08a84")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabajar con trazados: crear un trazado compuesto](https://www.youtube.com/watch?v=Io5bC0-nH6Q).  
  
##  <a name="Clipping"></a> Crear un trazado de recorte  
 Un trazado de recorte es un trazado o forma que se aplica a otro objeto, ocultando así las partes del objeto con máscara que sobresalen del trazado de recorte.  
  
 ![](../designers/media/22471e98-a841-4f39-a3ef-36090cf5a625.png "22471e98\-a841\-4f39\-a3ef\-36090cf5a625")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.png "BldAdminConsoleInitialConfigIcon") [Trabajar con trazados: crear un trazado de recorte](https://www.youtube.com/watch?v=Io5bC0-nH6Q#t=232).  
  
## Vea también  
 [Creación de una interfaz de usuario con Blend para Visual Studio](../designers/creating-a-ui-by-using-blend-for-visual-studio.md)