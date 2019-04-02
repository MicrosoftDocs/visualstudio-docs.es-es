---
title: Crear plantillas de varios proyectos
ms.date: 01/02/2018
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, creating multi-project
- project templates, multi-project
- multi-project templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4ef0dc772422322d8cfa2f8c7ca88a7cf30eab31
ms.sourcegitcommit: 489aca71046fb6e4aafd0a4509cd7dc149d707b1
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/25/2019
ms.locfileid: "58416258"
---
# <a name="how-to-create-multi-project-templates"></a>Procedimiento Crear plantillas de varios proyectos

Las plantillas de varios proyectos actúan como contenedores de dos o más proyectos. Cuando se crea un proyecto basado en una plantilla de varios proyectos, todos los proyectos de la plantilla se agregan a la solución.

Una plantilla de varios proyectos tiene como mínimo dos plantillas de proyectos y una plantilla raíz de tipo **ProjectGroup**.

Las plantillas de varios proyectos se comportan de forma distinta a las de proyecto único. Tienen las siguientes características únicas:

- A los proyectos individuales de una plantilla de varios proyectos no se les puede asignar nombres cuando la plantilla se usa para crear un proyecto. En su lugar, use el atributo **ProjectName** del elemento **ProjectTemplateLink** que hay en el archivo *vstemplate* para especificar un nombre para cada proyecto.

- Las plantillas de varios proyectos pueden contener proyectos para distintos lenguajes, pero la plantilla completa solo se puede colocar en una categoría. Especifique la categoría de plantilla en el elemento **ProjectType** del archivo *vstemplate*.

Una plantilla de varios proyectos debe incluir los elementos siguientes, comprimidos en un archivo *.zip*:

- Un archivo raíz *vstemplate* para toda la plantilla de varios proyectos. Este archivo raíz *vstemplate* contiene metadatos que se muestran en el cuadro de diálogo en que se crea un proyecto. También especifica dónde encontrar los archivos *vstemplate* de los proyectos de la plantilla. Este archivo debe estar ubicado en la raíz del archivo *.zip*.

- Dos o más carpetas que contienen los archivos necesarios para una plantilla de proyecto completa. Las carpetas incluyen todos los archivos de código del proyecto, así como un archivo *vstemplate* para el proyecto.

Por ejemplo, un archivo *.zip* de plantilla de varios proyectos que tiene dos proyectos podría tener los siguientes archivos y directorios:

- *MultiProjectTemplate.vstemplate*
- *\Project1\MyTemplate.vstemplate*
- *\Project1\Project1.vbproj*
- *\Project1\Class.vb*
- *\Project2\MyTemplate.vstemplate*
- *\Project2\Project2.vbproj*
- *\Project2\Class.vb*

El archivo raíz *vstemplate* de una plantilla de varios proyectos difiere de una plantilla de proyecto único de las siguientes formas:

- El atributo **Type** del elemento **VSTemplate** tiene el valor **ProjectGroup** en vez de **Project**. Por ejemplo:

    ```xml
    <VSTemplate Version="2.0.0" Type="ProjectGroup"
        xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    ```

- El elemento **TemplateContent** contiene un elemento **ProjectCollection** que tiene uno o varios elementos **ProjectTemplateLink** que definen las rutas de acceso a los archivos *vstemplate* de los proyectos incluidos. Por ejemplo:

    ```xml
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink>
                Project1\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink>
                Project2\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
    ```

## <a name="create-a-multi-project-template-from-an-existing-solution"></a>crear una plantilla de varios proyectos a partir de una solución existente

1. Cree una solución y agregue como mínimo dos proyectos.

2. Personalice los proyectos hasta que estén listos para exportarlos a una plantilla.

   > [!TIP]
   > Si usa [parámetros de plantilla](template-parameters.md) y quiere hacer referencia a variables de la plantilla principal, agregue el prefijo `ext_` al nombre del parámetro. Por ejemplo: `$ext_safeprojectname$`.

3. En el menú **Proyecto**, elija **Exportar plantilla**.

   Se abre el **Asistente para exportar plantillas**.

4. En la página **Elegir tipo de plantilla**, seleccione **Plantilla de proyecto**. Seleccione uno de los proyectos que quiera exportar a una plantilla y, después, haga clic en **Siguiente**. (Repita estos pasos con todos los proyectos de la solución).

5. En la página **Seleccionar opciones de plantilla**, escriba un nombre y, si quiere, una descripción, un icono y una imagen de vista previa para su plantilla. Elija **Finalizar**.

   El proyecto se exporta a un archivo *.zip* y se coloca en la ubicación de salida especificada.

   > [!NOTE]
   > Cada proyecto debe exportarse a una plantilla de forma individual; por lo tanto, debe repetir los pasos anteriores para cada proyecto de la solución.

6. Cree un directorio para la plantilla y un subdirectorio para cada proyecto.

7. Extraiga el contenido de cada archivo *.zip* del proyecto en el subdirectorio correspondiente que acaba de crear.

8. En el directorio base, cree un archivo XML que tenga le extensión de archivo *.vstemplate*. Ese archivo contiene los metadatos de la plantilla de varios proyectos. Vea el ejemplo que se indica a continuación para saber la estructura del archivo. Debe especificar la ruta de acceso relativa de cada archivo *vstemplate* del proyecto.

9. Seleccione todos los archivos del directorio base y, en el menú contextual, elija **Enviar a** > **Carpeta comprimida (en zip)**.

   Los archivos y las carpetas se comprimen en un archivo *.zip*.

10. Copie el archivo *.zip* en el directorio de plantillas de proyectos del usuario. De forma predeterminada, este directorio es *%USERPROFILE%\Documentos\Visual Studio \<versión\>\Templates\ProjectTemplates*.

11. En Visual Studio, elija **Archivo** > **Nuevo** > **Proyecto** y compruebe que aparece su plantilla.

## <a name="two-project-example"></a>Ejemplo de dos proyectos

En este ejemplo, se muestra un archivo raíz *vstemplate* básico de varios proyectos. En este ejemplo, la plantilla tiene dos proyectos: **Mi aplicación de Windows** y **Mi biblioteca de clases**. El atributo **ProjectName** del elemento **ProjectTemplateLink** especifica el nombre que se da al proyecto.

> [!TIP]
> Si no se especifica el atributo **ProjectName**, el nombre del archivo *vstemplate* se usa como nombre del proyecto.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <ProjectTemplateLink ProjectName="My Windows Application">
                WindowsApp\MyTemplate.vstemplate
            </ProjectTemplateLink>
            <ProjectTemplateLink ProjectName="My Class Library">
                ClassLib\MyTemplate.vstemplate
            </ProjectTemplateLink>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="example-with-solution-folders"></a>Ejemplo con carpetas de soluciones

En este ejemplo se usa el elemento **SolutionFolder** para dividir los proyectos en dos grupos: **Clases matemáticas** y **Clases gráficas**. La plantilla tiene cuatro proyectos, dos de los cuales se colocan en cada carpeta de soluciones.

```xml
<VSTemplate Version="2.0.0" Type="ProjectGroup"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>Multi-Project Template Sample</Name>
        <Description>An example of a multi-project template</Description>
        <Icon>Icon.ico</Icon>
        <ProjectType>VisualBasic</ProjectType>
    </TemplateData>
    <TemplateContent>
        <ProjectCollection>
            <SolutionFolder Name="Math Classes">
                <ProjectTemplateLink ProjectName="MathClassLib1">
                    MathClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="MathClassLib2">
                    MathClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
            <SolutionFolder Name="Graphics Classes">
                <ProjectTemplateLink ProjectName="GraphicsClassLib1">
                    GraphicsClassLib1\MyTemplate.vstemplate
                </ProjectTemplateLink>
                <ProjectTemplateLink ProjectName="GraphicsClassLib2">
                    GraphicsClassLib2\MyTemplate.vstemplate
                </ProjectTemplateLink>
            </SolutionFolder>
        </ProjectCollection>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [Crear plantillas para proyectos y elementos](../ide/creating-project-and-item-templates.md)
- [Cómo: Crear plantillas de proyecto](../ide/how-to-create-project-templates.md)
- [Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md)
- [Elemento SolutionFolder (plantillas de Visual Studio)](../extensibility/solutionfolder-element-visual-studio-templates.md)
- [Elemento ProjectTemplateLink (plantillas de Visual Studio)](../extensibility/projecttemplatelink-element-visual-studio-templates.md)