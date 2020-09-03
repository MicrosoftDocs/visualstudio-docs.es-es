---
title: 'Cómo: Crear plantillas de elementos | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- project item templates, XML reference
- project item templates, custom template locations
- project item templates, creating
- project item templates, metadata files
ms.assetid: 77bc53d4-d607-4820-a032-7e3b365891b5
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9edc79002a4a2d7c2fe135d7eb4669f5f010599
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72668076"
---
# <a name="how-to-create-item-templates"></a>Cómo: Crear plantillas de elementos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En los pasos del [primer procedimiento](#to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box) de este tema se muestra cómo crear una plantilla de elementos mediante el asistente **Exportar plantilla**. Si la plantilla consta de varios archivos, vea [Cómo: crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md).

 El asistente hace gran parte del trabajo de creación de la plantilla básica, pero en muchos casos deberá modificar manualmente el archivo .vstemplate después de haber exportado la plantilla. Por ejemplo, si quiere que el elemento aparezca en el cuadro de diálogo **Agregar nuevo elemento** de un proyecto de aplicación de [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)], tendrá que efectuar unos pasos adicionales. El [segundo procedimiento](#to-enable-the-item-template-to-be-used-in-a-store-project) de este tema le ayudará a realizar dicha tarea.

 En algunos casos es posible que quiera o deba crear una plantilla de elementos manualmente desde cero. En el [tercer procedimiento](#to-enable-templates-for-specific-project-sub-types) se muestra cómo hacerlo.

 Vea [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md) para obtener información sobre los elementos que se pueden usar en el archivo .vstemplate.

### <a name="to-add-a-custom-project-item-template-to-the-add-new-item-dialog-box"></a>Para agregar una plantilla de elemento de proyecto personalizada al cuadro de diálogo Agregar nuevo elemento

1. Cree o abra un proyecto en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

2. Agregue un elemento al proyecto y modifíquelo si lo desea.

3. Modifique el archivo de código para indicar dónde debe aplicarse el reemplazo de parámetros. Para obtener más información, vea [Cómo: sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).

4. En el menú **Archivo**, haga clic en **Exportar plantilla**.

5. Haga clic en **Plantilla de elemento**, seleccione el proyecto que contiene el elemento y haga clic en **Siguiente**.

6. Seleccione el elemento para el que quiere crear una plantilla y haga clic en **Siguiente**.

7. Seleccione las referencias de ensamblado que vaya a incluir en la plantilla y haga clic en **Siguiente**.

8. Escriba el nombre del archivo de icono, la imagen de vista previa, el nombre de la plantilla y la descripción de la misma y haga clic en **Finalizar**.

     Los archivos de la plantilla se agregan a un archivo .zip y se copian en cualquier directorio especificado en el cuadro de diálogo. La ubicación predeterminada es **. \Users \\<nombredeusuario \> \Documents\Visual Studio \<Version> \My Exported templates \\ ** Folder.

    > [!WARNING]
    > En versiones anteriores de Visual Studio, la ubicación predeterminada es **. \Users \\<nombredeusuario \> \Documents\Visual Studio \<Version> \Templates\ItemTemplates**.

### <a name="to-enable-the-item-template-to-be-used-in-a-store-project"></a>Para permitir que la plantilla de elementos se use en un proyecto de tienda

1. Siga los pasos del procedimiento anterior para exportar una plantilla de elementos.

2. Extraiga el archivo .vstemplate del archivo .zip que se copió en la carpeta \Users\\*nombreDeUsuario*\Documents\Visual Studio *Version*\Templates\ItemTemplates\ (o **My Exported Templates**).

3. Abra el archivo .vstemplate en Visual Studio.

4. Para un proyecto de C# de tienda Windows 8.1, en el archivo .vstemplate, agregue el siguiente XML entre las etiquetas de apertura y de cierre `<TemplateData>`: `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`.

    Un proyecto de tienda Windows 8.1 de C++ usa un valor de `WinRT-Native-6.3`. Para tipos de proyecto de Windows 10 y otros, vea [TemplateGroupID (Elemento, Plantillas de Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md).

    El ejemplo siguiente muestra el contenido completo de un archivo .vstemplate después de agregar la línea de código XML `<TemplateGroupID>WinRT-Managed</TemplateGroupID>`. Este ejemplo es específico de los proyectos de C#. Puede modificar los \<ProjectType> elementos y \< [TemplateGroupID](../extensibility/templategroupid-element-visual-studio-templates.md)> para especificar otros tipos de lenguaje y proyecto.

   ```xml
   <VSTemplate Version="3.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">
     <TemplateData>
       <DefaultName>MyItemStoreTemplate.xaml</DefaultName>
       <Name>MyItemStoreTemplate</Name>
       <Description>This is an example itemtemplate</Description>
       <ProjectType>CSharp</ProjectType>
       <SortOrder>10</SortOrder>
       <Icon>__TemplateIcon.ico</Icon>
       <TemplateGroupID>WinRT-Managed</TemplateGroupID>
     </TemplateData>
     <TemplateContent>
       <References />
       <ProjectItem SubType="Designer" TargetFileName="$fileinputname$.xaml" ReplaceParameters="true">MyItemTemplate.xaml</ProjectItem>
       <ProjectItem SubType="Code" TargetFileName="$fileinputname$.xaml.cs" ReplaceParameters="true">MyItemTemplate.xaml.cs</ProjectItem>
     </TemplateContent>
   </VSTemplate>
   ```

    Para ver otros valores posibles de TemplateGroupID, vea [TemplateGroupID (Elemento, Plantillas de Visual Studio)](../extensibility/templategroupid-element-visual-studio-templates.md). Para ver la referencia completa de .vstemplate, vea [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)

5. En Visual Studio, guarde el archivo .vstemplate y ciérrelo.

6. Vuelva a copiar y pegar el archivo .vstemplate en el archivo .zip que encontrará en la carpeta\Users\\*nombreDeUsuario*\Documents\Visual Studio *Version*\Templates\ItemTemplates\.

    Si aparece el cuadro de diálogo **Copiar archivo**, elija la opción **Copiar y reemplazar**.

   Ahora puede agregar un elemento basado en esta plantilla a un proyecto de [!INCLUDE[win8_appname_long](../includes/win8-appname-long-md.md)] mediante el cuadro de diálogo **Agregar nuevo elemento**.

   Para más información sobre los nombres de parámetro, vea [Parámetros de plantilla](../ide/template-parameters.md).

### <a name="to-enable-templates-for-specific-project-sub-types"></a>Para habilitar las plantillas para subtipos de proyecto específicos

1. El entorno de desarrollo le permite disponer de elementos de proyecto desde el cuadro de diálogo Agregar elemento de determinados proyectos. Use este procedimiento para disponer de elementos personalizados para proyectos de Windows, Web, Office o proyectos de bases de datos.

    Busque el elemento ProjectType en el archivo .vstemplate de la plantilla de elementos.

    Agregue un elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) inmediatamente después del elemento ProjectType.

2. Establezca el valor de texto del elemento en uno de los siguientes valores:

   1. Windows

   2. Office

   3. Base de datos

   4. Web

      Por ejemplo: `<ProjectSubType>Database</ProjectSubType>`.

      En el ejemplo siguiente se muestra una plantilla de elementos disponible para los proyectos de Office.

   ```
   <VSTemplate Version="2.0.0" Type="Item" Version="2.0.0">
       <TemplateData>
           <Name>Class</Name>
           <Description>An empty class file</Description>
           <Icon>Class.ico</Icon>
           <ProjectType>CSharp</ProjectType>
           <ProjectSubType>Office</ProjectSubType>
           <DefaultName>Class.cs</DefaultName>
       </TemplateData>
       <TemplateContent>
           <ProjectItem>Class1.cs</ProjectItem>
       </TemplateContent>
   </VSTemplate>

   ```

### <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Para crear manualmente una plantilla de elementos sin usar el Asistente para exportar plantillas

1. Cree un proyecto y un elemento de proyecto.

2. Modifique el elemento de proyecto hasta que se pueda guardar como plantilla.

3. Modifique el archivo de código según corresponda para indicar dónde debe aplicarse el reemplazo de parámetros. Para más información sobre el reemplazo de parámetros, vea Cómo: Sustituir parámetros en una plantilla.

4. Cree un archivo XML y guárdelo con la extensión de nombre de archivo .vstemplate en el mismo directorio que la nueva plantilla de elementos.

5. Cree el archivo XML .vstemplate para proporcionar los metadatos de la plantilla de elementos. Para más información, vea [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md) y el ejemplo de la sección anterior.

6. Guarde el archivo .vstemplate y ciérrelo.

7. En el Explorador de Windows, seleccione los archivos que desea incluir en la plantilla, haga clic con el botón secundario en la selección, haga clic en Enviar a y, a continuación, haga clic en Carpeta comprimida (en zip). Los archivos seleccionados se comprimen en un archivo .zip.

8. Copie el archivo .zip y péguelo en la ubicación de la plantilla de elementos del usuario. En Visual Studio 2015, el directorio predeterminado es ..\Users\\<nombreDeUsuario\>\Documents\Visual Studio 2015\Templates\ItemTemplates\\. Para más información, vea Cómo: Localizar y organizar plantillas de proyectos y de elementos.

## <a name="see-also"></a>Consulte también
 [Crear plantillas de proyecto y de elemento](../ide/creating-project-and-item-templates.md) [Cómo: crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md) [referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
