---
title: Establecer una imagen de fondo en un diagrama | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: fd9d5ca21dbe1b0444c650a127fc0184dfb640f1
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49240557"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Establecer una imagen de fondo en un diagrama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el SDK de visualización y modelado de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede establecer la imagen de fondo de un diseñador generado usando código personalizado.  
  
## <a name="setting-the-background-image"></a>Establecer la imagen de fondo  
  
#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Para establecer una imagen de fondo para un diseñador generado  
  
1.  Copie el archivo de imagen que quiere usar como fondo del diagrama en el directorio Dsl\Resources para el proyecto actual.  
  
2.  En **el Explorador de soluciones**, haga clic en la carpeta Dsl\Resources, elija **agregar**y, a continuación, haga clic en **elemento existente**.  
  
3.  En el **Agregar elemento existente** cuadro de diálogo, vaya a la carpeta Dsl\Resources.  
  
4.  En el **archivos de tipo** lista, haga clic en **archivos de imagen**.  
  
5.  Haga clic en el archivo de imagen que ha copiado en el directorio y, a continuación, haga clic en **agregar**.  
  
6.  Haga clic en Dsl y haga clic en **propiedades** para abrir las propiedades del proyecto de Dsl.  
  
7.  En el **recursos** , haga clic **este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear uno.**  
  
8.  Agregue el archivo de imagen al archivo de recursos arrastrando la imagen desde **el Explorador de soluciones** en la ventana de recursos.  
  
9. Abra el menú Archivo y haga clic en la opción para guardar las propiedades del proyecto.  
  
10. Compruebe que el archivo Dsl\Properties\Resources.resx existe y que tiene el archivo Resources.Designer.cs debajo de él.  
  
11. Si Resources.Designer.cs no está, haga clic en el archivo Resources.resx en **el Explorador de soluciones**.  
  
12. En la ventana **Propiedades** , establezca la propiedad `Custom Tool` en `ResXFileCodeGenerator`.  
  
13. En **el Explorador de soluciones**, haga clic en el proyecto de Dsl, seleccione **agregar**y haga clic en **nueva carpeta**.  
  
14. Nombre de la carpeta **personalizado**.  
  
15. Haga clic en la carpeta Custom, elija **agregar**y haga clic en **nuevo elemento**.  
  
16. En el **Agregar nuevo elemento** cuadro de diálogo el **plantillas** lista, haga clic en **archivo de código**.  
  
17. En el **nombre** , escriba `BackgroundImage.cs`y haga clic en **agregar**.  
  
18. Copie el código siguiente en el archivo BackgroundImage.cs y ajuste el espacio de nombres, el nombre de la clase de diagrama y el nombre del recurso de archivo de imagen.  
  
     Reemplace "MyDiagramClass" por el nombre de la clase parcial de diagrama definida en Dsl\GeneratedCode\Diagrams.cs. También puede recuperar el espacio de nombres correcto del archivo Dsl\GeneratedCode\Diagrams.cs.  
  
    ```  
    using System;  
    using Microsoft.VisualStudio.Modeling.Diagrams;  
  
    // Fix the namespace:  
    namespace Fabrikam.MyLanguage  
    {  
      // Fix the Diagram Class name - get it from GeneratedCode\Diagram.cs  
  
      public partial class Language29Diagram  
      {  
        protected override void InitializeInstanceResources()  
        {  
          // Fix the Resources namespace and the Image resource name:  
          ImageField backgroundField = new ImageField("background",  
              Fabrikam.MyLanguage.Properties.Resources.MyPicture);  
  
          backgroundField.DefaultFocusable = false;  
          backgroundField.DefaultSelectable = false;  
          backgroundField.DefaultVisibility = true;  
          backgroundField.DefaultUnscaled = false;  
  
          shapeFields.Add(backgroundField);  
  
          backgroundField.AnchoringBehavior  
            .SetTopAnchor(AnchoringBehavior.Edge.Top, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetLeftAnchor(AnchoringBehavior.Edge.Left, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetRightAnchor(AnchoringBehavior.Edge.Right, 0.01);  
          backgroundField.AnchoringBehavior  
            .SetBottomAnchor(AnchoringBehavior.Edge.Bottom, 0.01);  
  
          base.InitializeInstanceResources();  
        }  
      }  
    }  
    ```  
  
     Para obtener más información acerca de cómo personalizar el modelo con el código de programa, consulte [navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md).  
  
## <a name="see-also"></a>Vea también  
 [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)   
 [Personalizar campos de imagen y texto](../modeling/customizing-text-and-image-fields.md)   
 [Navegar y actualizar un modelo en el código de programa](../modeling/navigating-and-updating-a-model-in-program-code.md)   
 [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)



