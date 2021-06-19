---
title: Establecer una imagen de fondo en un diagrama
description: Aprenda que en el SDK Visual Studio visualización y modelado, puede establecer la imagen de fondo de un diseñador generado mediante código personalizado.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 9304117932b92408f12a23747253de66dfd767d1
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385674"
---
# <a name="setting-a-background-image-on-a-diagram"></a>Establecer una imagen de fondo en un diagrama
En Visual Studio SDK de visualización y modelado, puede establecer la imagen de fondo de un diseñador generado mediante código personalizado.

## <a name="setting-the-background-image"></a>Establecer la imagen de fondo

#### <a name="to-set-a-background-image-for-a-generated-designer"></a>Para establecer una imagen de fondo para un diseñador generado

1. Copie el archivo de imagen que quiere usar como fondo del diagrama en el directorio Dsl\Resources para el proyecto actual.

2. En **Explorador de soluciones**, haga clic con el botón derecho en la carpeta Dsl\Resources, seleccione Agregar **y,** a continuación, haga clic en **Elemento existente.**

3. En el **cuadro de diálogo Agregar elemento** existente, vaya a la carpeta Dsl\Resources.

4. En la **lista Archivos de tipo** , haga clic en Archivos de **imagen**.

5. Haga clic en el archivo de imagen que copió en el directorio y, a continuación, haga clic **en Agregar**.

6. Haga clic con el botón derecho en Dsl y haga clic **en Propiedades** para abrir las propiedades del proyecto dsl.

7. En la **pestaña Recursos,** haga clic **en Este proyecto no contiene un archivo de recursos predeterminado. Haga clic aquí para crear uno.**

8. Agregue el archivo de imagen al archivo de recursos arrastrando la imagen **Explorador de soluciones** a la ventana de recursos.

9. Abra el menú Archivo y haga clic en la opción para guardar las propiedades del proyecto.

10. Compruebe que el archivo Dsl\Properties\Resources.resx existe y que tiene el archivo Resources.Designer.cs debajo de él.

11. Si falta Resources.Designer.cs, haga clic en el archivo Resources.resx **Explorador de soluciones**.

12. En la ventana **Propiedades** , establezca la propiedad `Custom Tool` en `ResXFileCodeGenerator`.

13. En **Explorador de soluciones**, haga clic con el botón derecho en el proyecto Dsl, **seleccione Agregar** y haga clic en Nueva **carpeta**.

14. Asigne a la carpeta el **nombre Custom**.

15. Haga clic con el botón derecho en la carpeta Personalizada, **seleccione Agregar** y haga clic en **Nuevo elemento.**

16. En el cuadro **de diálogo Agregar nuevo** elemento , en la lista **Plantillas** , haga clic en Archivo **de código**.

17. En el **cuadro Nombre** , escriba y haga clic `BackgroundImage.cs` en **Agregar**.

18. Copie el código siguiente en el archivo BackgroundImage.cs y ajuste el espacio de nombres, el nombre de la clase de diagrama y el nombre del recurso de archivo de imagen.

     Reemplace "MyDiagramClass" por el nombre de la clase parcial de diagrama definida en Dsl\GeneratedCode\Diagrams.cs. También puede recuperar el espacio de nombres correcto del archivo Dsl\GeneratedCode\Diagrams.cs.

    ```csharp
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

     Para obtener más información sobre cómo personalizar el modelo con código de programa, vea Navegar y [actualizar un modelo en código de programa.](../modeling/navigating-and-updating-a-model-in-program-code.md)

## <a name="see-also"></a>Vea también

- [Definir formas y conectores](../modeling/defining-shapes-and-connectors.md)
- [Personalizar campos de texto y de imagen](../modeling/customizing-text-and-image-fields.md)
- [Navegar y actualizar un modelo en el código del programa](../modeling/navigating-and-updating-a-model-in-program-code.md)
- [Escribir código para personalizar lenguajes específicos de dominio](../modeling/writing-code-to-customise-a-domain-specific-language.md)

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]
