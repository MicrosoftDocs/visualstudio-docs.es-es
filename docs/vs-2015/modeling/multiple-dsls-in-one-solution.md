---
title: Varios DSL en una solución | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7e668620-6217-4e87-aea7-e9036776c8e4
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 8bf5e3d69b67cf51c1e70ec8ffe9e91d87a1dcbe
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49820179"
---
# <a name="multiple-dsls-in-one-solution"></a>Varios DSL en una solución
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede empaquetar varios DSL como parte de una única solución para que se instalen juntos.  
  
 Puede usar varias técnicas para integrar varios DSL. Para obtener más información, consulte [integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md) y [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md) y [personalizar el comportamiento de copia](../modeling/customizing-copy-behavior.md).  
  
### <a name="to-build-more-than-one-dsl-in-the-same-solution"></a>Para compilar más de un DSL en la misma solución  
  
1. Cree dos o más soluciones de DSL y un proyecto de VSIX, y agregue todos los proyectos a una única solución.  
  
   -   Para crear un nuevo proyecto VSIX: en el **nuevo proyecto** cuadro de diálogo, seleccione **Visual C#**, **extensibilidad**, **proyecto VSIX**.  
  
   -   Cree dos o más soluciones de DSL en el directorio de soluciones VSIX.  
  
        Por cada DSL, abra una nueva instancia de Visual Studio. Cree el nuevo DSL y especifique la misma carpeta de solución que la solución de VSIX.  
  
        Asegúrese de crear cada DSL con una extensión de nombre de archivo diferente.  
  
   -   Cambiar los nombres de los **Dsl** y **DslPackage** proyectos para que sean todos diferentes. Por ejemplo: `Dsl1`, `DslPackage1`, `Dsl2`, `DslPackage2`.  
  
   -   En cada **DslPackage\*\source.extension.tt**, actualice esta línea con el nombre de proyecto de Dsl correcto:  
  
        `string dslProjectName = "Dsl2";`  
  
   -   En la solución VSIX, agregue el Dsl * y DslPackage\* proyectos.  
  
        Quizás quiera coloca cada par en su propia carpeta de solución.  
  
2. Combine los manifiestos VSIX de los DSL:  
  
   1.  Abra _Suproyectovsix_**\source.extension.manifest**.  
  
   2.  Para cada DSL, elija **agregar contenido** y agregue:  
  
       -   `Dsl*` un proyecto como un **componente MEF**  
  
       -   `DslPackage*` un proyecto como un **componente MEF**  
  
       -   `DslPackage*` un proyecto como un **VS Package**  
  
3. Compile la solución.  
  
   El VSIX resultante instalará ambos DSL. Puede probarlos mediante F5 o implementar _Suproyectovsix_**\bin\Debug\\\*.vsix**.  
  
## <a name="see-also"></a>Vea también  
 [Integrar modelos utilizando Modelbus de Visual Studio](../modeling/integrating-models-by-using-visual-studio-modelbus.md)   
 [Cómo: agregar un controlador de arrastrar y colocar](../modeling/how-to-add-a-drag-and-drop-handler.md)   
 [Personalizar comportamiento de copia](../modeling/customizing-copy-behavior.md)



