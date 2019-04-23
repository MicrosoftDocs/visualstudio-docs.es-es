---
title: Insertar controles y modificar su comportamiento en el Diseñador XAML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-designers
ms.topic: conceptual
ms.assetid: a80fff74-bf01-41c9-ab85-ada7a873c3a9
caps.latest.revision: 17
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 219d70f1a722a19017399ab851aa2e69c44d2b28
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/17/2019
ms.locfileid: "59663367"
---
# <a name="insert-controls-and-modify-their-behavior-in-xaml-designer"></a>Insertar controles y modificar su comportamiento en el Diseñador XAML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los controles permiten a los usuarios interactuar con la aplicación. Puede utilizarlos para recopilar información y realizar acciones como animar un objeto o realizar una consulta en un origen de datos.  
  
 **En este tema:**  
  
-   [Agregar controles a la mesa de trabajo](#Insert)  
  
-   [Acciones de los controles](#Modify)  
  
##  <a name="Insert"></a> Agregar controles a la mesa de trabajo  
 Puede arrastrar controles desde el panel **Activos** a la **mesa de trabajo**y, a continuación, modificarlos en la ventana **Propiedades** .  
  
 ![Blend &#45; Activos &#45; FlipView](../designers/media/blend-assetsflipview-xaml.png "blend_AssetsFlipView_XAML")  
  
 En estos vídeos se enseña cómo usar algunos de los controles más comunes.  
  
|Control|Vea un vídeo corto|  
|-------------|-------------------------|  
|`Menu` ![](../designers/media/015a263c-0b2b-4253-ac57-b86fcb8c9591.png "015a263c-0b2b-4253-ac57-b86fcb8c9591")|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Agregar los controles](https://www.youtube.com/watch?v=ra4AHfgD4Ys&list=PLBDF977B2F1DAB358&index=45)|  
|`Button` ![](../designers/media/05df1779-a68f-436b-b834-a91b7995a3ec.png "05df1779-a68f-436b-b834-a91b7995a3ec")|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Diseñar un botón](http://www.popscreen.com/v/6A4gb/Microsoft-Expression-Blend-Designing-a-Button)|  
|`Textblock` ![](../designers/media/42165963-00f7-4a33-abcd-b0849edebada.png "42165963-00f7-4a33-abcd-b0849edebada")|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Agregar imágenes a un bloque de texto](http://www.popscreen.com/v/6A4du/Microsoft-Expression-Blend-Adding-Images-to-a-TextBlock)|  
|`Slider` ![](../designers/media/bf689d92-3c74-4218-815c-e98c930ac189.png "bf689d92-3c74-4218-815c-e98c930ac189")|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Crear un control deslizante con información sobre herramientas](http://www.bing.com/videos/search?q=slider%20expression%20blend&qs=n&form=QBVR&pq=slider%20expression%20blend&sc=1-23&sp=-1&sk=#view=detail&mid=F1BB7DB91B2772A8CA2AF1BB7DB91B2772A8CA2A)|  
|`GridSplitter` ![](../designers/media/d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be.png "d08d529f-a27e-4a8f-95aa-8a4e8b4ee7be")|![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [Trabajar con GridSplitter](https://www.youtube.com/watch?v=bf4t6c8ms2w)|          

### <a name="make-a-control-out-of-an-image-shape-or-path"></a>Crear un control a partir de una imagen, una forma o un trazado  
 Puede convertir cualquier objeto en un control.  
  
 ![Cuadro de diálogo Convertir en control de Blend](../designers/media/blend-makeintocontrol-xaml.png "blend_MakeIntoControl_XAML")  
  
 Imagine, por ejemplo, la imagen de una televisión en el centro de una página. A partir de imágenes pequeñas podría crear controles que tuviesen el aspecto de botones de televisión y en los que los usuarios podrían hacer clic para cambiar de canal.  
  
 Esto es posible porque los botones ahora son controles que permiten responder a las interacciones del usuario; en este caso, al hacer clic en un botón.  
  
 Para crear un control, seleccione un objeto. A continuación, en el menú **Herramientas** , haga clic en **Crear control**.  
  
##  <a name="Modify"></a> Acciones de los controles  
 Los controles pueden realizar acciones cuando los usuarios interactúan con ellos. Por ejemplo, pueden iniciar una animación, actualizar un origen de datos o reproducir un vídeo.  
  
 Utilice *desencadenadores*, *comportamientos*y *eventos* para que los controles realicen accines.  
  
### <a name="triggers"></a>desencadenadores  
 Un *desencadenador* cambia una propiedad o realiza una tarea en respuesta a un evento o a un cambio en otra propiedad. Por ejemplo, puede cambiar el color de un botón cuando los usuarios se mantenga el ratón sobre él.  
  
 ![El panel "Desencadenadores"](../designers/media/custom-button-blend-propertytriggerinfo.png "custom_button_blend_PropertyTriggerInfo")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [agregar un desencadenador de propiedad](http://www.popscreen.com/v/6A4gO/Microsoft-Expression-Blend-Adding-a-Property-Trigger).  
  
### <a name="behaviors"></a>comportamientos  
 Un *comportamiento* es un paquete de código reutilizable. Es un poco más completo que cambiar las propiedades y puede realizar acciones como consultas a un servicio de datos. Blend trae incorporada una pequeña colección de comportamientos, pero se pueden agregar más. Arrastre un comportamiento a cualquier objeto de la mesa de trabajo y después personalícelo mediante la configuración de sus propiedades.  
  
 ![FluidMoveBehavior en el panel Propiedades](../designers/media/b4-fluidmovebehaviorproperties-sample.png "b4_FluidMoveBehaviorProperties_Sample")  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [consejos de Blend: Introducción al uso de comportamientos, parte 1](http://www.bing.com/videos/search?q=Expression%20blend%20behaviors&qs=n&form=QBVR&pq=expression%20blend%20behavior&sc=4-25&sp=-1&sk=#view=detail&mid=CF0DD797ED84DE740904CF0DD797ED84DE740904).  
  
### <a name="events"></a>Eventos  
 Para una flexibilidad óptima, controle un *evento*. Tendrá que escribir código.  
  
 **Vea un vídeo corto:** ![Configurar las características instaladas](../designers/media/bldadminconsoleinitialconfigicon.PNG "BldAdminConsoleInitialConfigIcon") [agregar un evento del Mouse](https://www.youtube.com/watch?v=2PMxAlb-x_E).
