---
title: Creación de plantillas web para Visual Studio
ms.date: 01/02/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio templates, Web
- templates [Visual Studio], Web
- Web templates [Visual Studio]
- project templates [Visual Studio], Web
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: d092234c183c93ce99e7d864c71c64a332aeb758
ms.sourcegitcommit: 5b767247b3d819a99deb0dbce729a0562b9654ba
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/20/2018
ms.locfileid: "39178948"
---
# <a name="how-to-manually-create-web-templates"></a>Cómo: Crear plantillas web manualmente

La creación de una plantilla web es diferente de la creación de otros tipos de plantillas. Dado que las plantillas de proyecto web aparecen en el cuadro de diálogo **Agregar nuevo sitio web** y los elementos de proyecto web se clasifican por lenguaje de programación, el archivo *vstemplate* debe especificar la plantilla como una plantilla web e identificar el lenguaje de programación.

> [!NOTE]
> Las plantillas web deben contener un archivo *.webproj* vacío, y debe hacerse referencia a dicho archivo en el archivo *vstemplate* del atributo `File` del elemento `Project`. Aunque para los proyectos web no se necesita un archivo de proyecto *.proj*, es necesario crear este archivo de código auxiliar para que la plantilla web funcione correctamente.

## <a name="to-manually-create-a-web-template"></a>Para crear una plantilla web manualmente

1. Cree un proyecto web.

1. Modifique o elimine los archivos del proyecto, o bien agregue nuevos archivos al proyecto.

1. Cree un archivo XML y guárdelo con la extensión de nombre de archivo *vstemplate* en el mismo directorio del proyecto. No lo agregue al proyecto en Visual Studio.

1. Edite el archivo XML *.vstemplate* para proporcionar los metadatos de la plantilla de proyecto. Para obtener más información, vea el [siguiente ejemplo](#example).

1. Busque el elemento `ProjectType` en el archivo *vstemplate* y establezca el valor de texto en `Web`.

1. Después del elemento `ProjectType`, agregue un elemento `ProjectSubType` y establezca el valor de texto en el lenguaje de programación de la plantilla. El lenguaje de programación puede ser uno de estos valores:

    - CSharp
    - VisualBasic

    Por ejemplo:

    ```xml
    <TemplateData>
        ...
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        ...
    </TemplateData>
    ```

1. Seleccione los archivos de la plantilla (incluido el archivo *vstemplate*), haga clic con el botón derecho en la selección y elija **Enviar a** > **Carpeta comprimida (en zip)**. Los archivos se comprimen en un archivo *.zip*.

1. Coloque el archivo de plantilla *.zip* en el directorio de plantillas de proyecto de Visual Studio. De forma predeterminada, este directorio es *%USERPROFILE%\Documentos\Visual Studio \<versión\>\ProjectTemplates*.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra un archivo *vstemplate* básico para una plantilla de proyecto web:

```xml
<VSTemplate Version="2.0.0" Type="Project"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>
    <TemplateData>
        <Name>MyWebProjecStarterKit</Name>
        <Description>A simple web template</Description>
        <Icon>icon.ico</Icon>
        <ProjectType>Web</ProjectType>
        <ProjectSubType>CSharp</ProjectSubType>
        <DefaultName>WebSite</DefaultName>
    </TemplateData>
    <TemplateContent>
        <Project File="WebApplication.webproj">
            <ProjectItem>icon.ico</ProjectItem>
            <ProjectItem OpenInEditor="true">Default.aspx</ProjectItem>
            <ProjectItem>Default.aspx.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también

- [Creación de plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md)