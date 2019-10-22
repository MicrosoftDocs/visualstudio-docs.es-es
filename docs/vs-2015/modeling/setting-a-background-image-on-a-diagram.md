---
title: Establecer una imagen de fondo en un diagrama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: e334a24c-8521-4072-b50f-e59158dde145
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 2b7d206852101a1d99a08eac710d88e93afe4a04
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72671203"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Establecer una imagen de fondo en un diagrama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En el SDK de visualización y modelado de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] puede establecer la imagen de fondo de un diseñador generado usando código personalizado.

## <a name="setting-the-background-image"></a>Establecer la imagen de fondo

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Para establecer una imagen de fondo para un diseñador generado

1. Copie el archivo de imagen que quiere usar como fondo del diagrama en el directorio Dsl\Resources para el proyecto actual.

2. En **Explorador de soluciones**, haga clic con el botón secundario en la carpeta Dsl\Resources, seleccione **Agregar**y, a continuación, haga clic en **elemento existente**.

3. En el cuadro de diálogo **Agregar elemento existente** , vaya a la carpeta Dsl\Resources.

4. En la lista **tipos de archivo** , haga clic en **archivos de imagen**.

5. Haga clic en el archivo de imagen que copió en el directorio y, a continuación, haga clic en **Agregar**.

6. Haga clic con el botón derecho en DSL y haga clic en **propiedades** para abrir las propiedades del proyecto DSL.

7. En la pestaña **recursos** , haga clic en **este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear uno.**

8. Agregue el archivo de imagen al archivo de recursos arrastrando la imagen desde **Explorador de soluciones** a la ventana recursos.

9. Abra el menú Archivo y haga clic en la opción para guardar las propiedades del proyecto.

10. Compruebe que el archivo Dsl\Properties\Resources.resx existe y que tiene el archivo Resources.Designer.cs debajo de él.

11. Si falta Resources.Designer.cs, haga clic en el archivo resources. resx en **Explorador de soluciones**.

12. En la ventana **Propiedades** , establezca la propiedad `Custom Tool` en `ResXFileCodeGenerator`.

13. En **Explorador de soluciones**, haga clic con el botón secundario en el proyecto DSL, elija **Agregar**y haga clic en **nueva carpeta**.

14. Asigne a la carpeta el nombre **Custom**.

15. Haga clic con el botón secundario en la carpeta personalizada, seleccione **Agregar**y haga clic en **nuevo elemento**.

16. En el cuadro de diálogo **Agregar nuevo elemento** , en la lista **plantillas** , haga clic en **archivo de código**.

17. En el cuadro **nombre** , escriba `BackgroundImage.cs` y haga clic en **Agregar**.

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

     Para obtener más información sobre cómo personalizar el modelo con código de programa, vea [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md).

## <a name="see-also"></a>Vea también
 [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md) [personalizar los campos de texto e imagen](../modeling/customizing-text-and-image-fields.md) [navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md) [escribir código para personalizar un lenguaje específico del dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)
