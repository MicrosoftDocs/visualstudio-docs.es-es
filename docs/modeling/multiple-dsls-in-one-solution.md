---
title: "Varios DSL en una soluci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 3
---
# Varios DSL en una soluci&#243;n
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede empaquetar varios DSL como parte de una única solución para que se instalen juntos.  
  
 Puede usar varias técnicas para integrar varios DSL.  Para obtener más información, vea [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md), [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) y [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md).  
  
### Para compilar más de un DSL en la misma solución  
  
1.  Cree dos o más soluciones de DSL y un proyecto de VSIX, y agregue todos los proyectos a una única solución.  
  
    -   Para crear un nuevo proyecto de VSIX: En el cuadro de diálogo **Nuevo proyecto**, elija **Visual C\#**, **Extensibilidad**, **Proyecto VSIX**.  
  
    -   Cree dos o más soluciones de DSL en el directorio de soluciones VSIX.  
  
         Por cada DSL, abra una nueva instancia de Visual Studio.  Cree el nuevo DSL y especifique la misma carpeta de solución que la solución de VSIX.  
  
         Asegúrese de crear cada DSL con una extensión de nombre de archivo diferente.  
  
    -   Cambie los nombres de los proyectos **Dsl** y **DslPackage** para que sean todos diferentes.  Por ejemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
    -   En cada **DslPackage\*\\source.extension.tt**, actualice esta línea con el nombre de proyecto de DSL correcto:  
  
         `string dslProjectName = "Dsl2";`  
  
    -   En la solución de VSIX, agregue los proyectos Dsl\* y DslPackage\*.  
  
         Quizás quiera coloca cada par en su propia carpeta de solución.  
  
2.  Combine los manifiestos VSIX de los DSL:  
  
    1.  Abra *suProyectoVsix***\\source.extension.manifest**.  
  
    2.  Para cada DSL, elija **Agregar contenido** y agregue:  
  
        -   El proyecto `Dsl*` como un **MEF Component** \(Componente MEF\).  
  
        -   El proyecto `DslPackage*` como un **MEF Component** \(Componente MEF\).  
  
        -   El proyecto `DslPackage*` como un **VS Package** \(Paquete de VS\).  
  
3.  Compile la solución.  
  
 El VSIX resultante instalará ambos DSL.  Use F5 para probarlos o implemente *suProyectoVsix***\\bin\\Debug\\\*.vsix**.  
  
## Vea también  
 [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Cómo: Agregar un controlador para arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)