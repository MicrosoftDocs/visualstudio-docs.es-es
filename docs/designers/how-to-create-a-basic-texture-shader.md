---
title: "Cómo: Crear un sombreador de textura básico | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-designers
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5af113fb-6415-4be0-8b23-10fddb10e80a
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 52e909e911a552b69930ef6a60257fca29a0794d
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-basic-texture-shader"></a>Cómo: Crear un sombreador de textura básico
En este documento se muestra cómo usar el Diseñador de sombras y el lenguaje DGSL (Directed Graph Shader Language) para crear un sombreador de una textura. Este sombreador establece directamente el color final en los valores RGB y alfa muestreados de la textura.  
  
 Este documento muestra estas actividades:  
  
-   Quitar nodos de un gráfico de sombreador  
  
-   Agregar nodos a un gráfico  
  
-   Establecer los parámetros del sombreador  
  
-   Establecer la visibilidad del parámetro  
  
-   Conectar nodos  
  
## <a name="creating-a-basic-texture-shader"></a>Crear un sombreador de textura básico  
 Puede implementar un sombreador básico de una sola textura escribiendo los valores de color y alfa de una muestra de textura directamente en el color de salida final.  
  
 Antes de empezar, asegúrese de que se muestran la ventana **Propiedades** y el **Cuadro de herramientas**.  
  
#### <a name="to-create-a-basic-texture-shader"></a>Para crear un sombreador de textura básico  
  
1.  Cree un sombreador DGSL con el que trabajar. Para obtener información sobre cómo agregar un sombreador DGSL al proyecto, vea la sección Introducción de [Diseñador de sombras](../designers/shader-designer.md).  
  
2.  Elimine el nodo **Color de punto**. En el modo **Seleccionar**, seleccione el nodo **Color de punto** y, después, en la barra de menús, elija **Editar**, **Eliminar**. Esto hace sitio para el nodo que se agrega en el paso siguiente.  
  
3.  Agregue un nodo **Muestra de textura** al gráfico. En el **Cuadro de herramientas**, en **Textura**, seleccione **Muestra de textura** y muévala a la superficie de diseño.  
  
4.  Agregue un nodo **Coordenada de textura** al gráfico. En el **Cuadro de herramientas**, en **Textura**, seleccione **Coordenada de textura** y muévala a la superficie de diseño.  
  
5.  Elija una textura para aplicar. En el modo **Seleccionar**, seleccione el nodo **Muestra de textura** y, después, en la ventana **Propiedades**, especifique la textura que quiere usar mediante la propiedad **Nombre de archivo**.  
  
6.  Cree la textura públicamente accesible. Seleccione el nodo **Muestra de textura** y, después, en la ventana **Propiedades**, establezca la propiedad **Acceso** en **Público**. Ahora puede configurar la textura desde otra herramienta, como el **Editor de modelos**.  
  
7.  Conecte las coordenadas de textura a la muestra de textura. En el modo **Seleccionar**, mueva el terminal **Salida** del nodo **Coordenada de textura** al terminal **UV** del nodo **Muestra de textura**. Esta conexión muestrea la textura en las coordenadas especificadas.  
  
8.  Conecte la muestra de textura al color final. Mueva el terminal **RGB** del nodo **Muestra de textura** al terminal **RGB** del nodo **Color final** y, después, mueva el terminal **Alfa** del nodo **Muestra de textura** al terminal **Alfa** del nodo **Color final**.  
  
 La ilustración siguiente muestra el gráfico de sombreador completo y una vista previa del sombreador aplicado a un cubo.  
  
> [!NOTE]
>  En esta ilustración, se usó un plano como la forma de vista previa y se especificó una textura para demostrar mejor el efecto del sombreador.  
  
 ![Gráfico de sombreador y vista previa de su efecto](../designers/media/digit-texture-effect.png "Digit-Texture-Effect")  
  
 Es posible que algunas formas proporcionen mejores vistas previas para algunos sombreadores. Para más información sobre cómo obtener una vista previa de los sombreadores en el Diseñador de sombras, vea [Diseñador de sombras](../designers/shader-designer.md)  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Aplicar un sombreador a un modelo 3D](../designers/how-to-apply-a-shader-to-a-3-d-model.md)   
 [Editor de imágenes](../designers/image-editor.md)   
 [Diseñador de sombras](../designers/shader-designer.md)   
 [Nodos del Diseñador de sombras](../designers/shader-designer-nodes.md)