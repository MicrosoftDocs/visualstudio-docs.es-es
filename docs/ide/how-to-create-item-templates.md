---
title: "Creación de plantillas de elemento para Visual Studio | Microsoft Docs"
ms.custom: 
ms.date: 01/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: item templates [Visual Studio], creating
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8fd5d7fba092df5accfaad9d26cfc05f196981ba
ms.sourcegitcommit: 11740fed01cc602252ef698aaa11c07987b00570
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/12/2018
---
# <a name="how-to-create-item-templates"></a>Cómo: Crear plantillas de elemento

En este tema se muestra cómo crear una plantilla de elemento con el **Asistente para exportar plantillas**. Si la plantilla consta de varios archivos, vea [Cómo: Crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md).

## <a name="to-add-a-user-item-template-to-the-add-new-item-dialog-box"></a>Para agregar una plantilla de elemento de usuario al cuadro de diálogo Agregar nuevo elemento

1. Cree o abra un proyecto en Visual Studio.

1. Agregue un elemento al proyecto y, si quiere, modifíquelo.

1. Modifique el archivo de código para indicar dónde debe aplicarse el reemplazo de parámetros. Para obtener más información, vea [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).

1. En el menú **Proyecto**, elija **Exportar plantilla...**.

1. En la página **Elegir tipo de plantilla**, seleccione **Plantilla de elemento**, seleccione el proyecto que contiene el elemento y seleccione **Siguiente**.

1. En la página **Seleccionar elemento para exportar**, seleccione el elemento para el que quiera crear una plantilla y seleccione **Siguiente**.

1. En la página **Seleccionar referencias de elemento**, seleccione las referencias de ensamblado que quiera incluir en la plantilla y seleccione **Siguiente**.

1. En la página **Seleccionar opciones de plantilla**, indique el nombre de esta y una descripción opcional, una imagen de icono, una imagen de vista previa y seleccione **Finalizar**.

    Los archivos de la plantilla se agregan a un archivo .zip y se copian en el directorio especificado en el asistente. La ubicación predeterminada es %USERPROFILE%\Documentos\Visual Studio \<versión\>\My Exported Templates.

1. Si no ha seleccionado la opción **Importar automáticamente la plantilla en Visual Studio** en el **Asistente para exportar plantillas**, localice la plantilla exportada y cópiela en el directorio de plantilla de elemento del usuario. La ubicación predeterminada es %USERPROFILE%\Documentos\Visual Studio \<versión\>\Templates\ItemTemplates.

1. Cierre Visual Studio y vuelva a abrirlo.

1. Cree un proyecto o abra uno existente, seleccione **Proyecto** > **Agregar elemento nuevo...** o presione **Ctrl** + **Mayús** + **A**.

   La plantilla de elemento aparece en el cuadro de diálogo **Agregar nuevo elemento**. Si ha agregado una descripción en el **Asistente para exportar plantillas**, la descripción aparecerá en la parte derecha del cuadro de diálogo.

## <a name="to-enable-the-item-template-to-be-used-in-a-universal-windows-app-project"></a>Para permitir que se use la plantilla de elemento en un proyecto de Aplicación universal de Windows

El asistente hace gran parte del trabajo de creación de una plantilla básica, pero en muchos casos deberá modificar manualmente el archivo .vstemplate después de haber exportado la plantilla. Por ejemplo, si quiere que el elemento aparezca en el cuadro de diálogo **Agregar nuevo elemento** de un proyecto de Aplicación universal de Windows, tendrá que efectuar unos pasos adicionales.

1. Siga los pasos de la sección anterior para exportar una plantilla de elemento.

1. Extraiga el archivo comprimido creado y abra el archivo .vstemplate en Visual Studio.

1. Para un proyecto de C# de Windows universal, agregue el siguiente XML en el elemento `<TemplateData>`:

   ```xml
   <TemplateID>Microsoft.CSharp.Class</TemplateID>
   ```

1. En Visual Studio, guarde el archivo .vstemplate y ciérrelo.

1. Copie y pegue el archivo .vstemplate en el archivo .zip.

     Si aparece el cuadro de diálogo **Copiar archivo**, elija la opción **Copiar y reemplazar**.

Ahora puede agregar un elemento basado en esta plantilla a un proyecto de Windows universal desde el cuadro de diálogo **Agregar nuevo elemento**.

## <a name="to-enable-templates-for-specific-project-subtypes"></a>Para habilitar las plantillas para subtipos de proyecto específicos

Puede especificar que la plantilla solo debería aparecer para determinados subtipos de proyecto, como Windows, Office, base de datos o web.

1. Busque el elemento ProjectType en el archivo .vstemplate de la plantilla de elementos.

1. Agregue un elemento [ProjectSubType](../extensibility/projectsubtype-element-visual-studio-templates.md) inmediatamente después del elemento ProjectType.

1. Establezca el valor de texto del elemento en uno de los siguientes valores:

    - Windows
    - Office
    - Base de datos
    - Web

Por ejemplo: `<ProjectSubType>Database</ProjectSubType>`.

En el ejemplo siguiente se muestra una plantilla de elementos para los proyectos de **Office**.

```xml
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

## <a name="to-manually-create-an-item-template-without-using-the-export-template-wizard"></a>Para crear manualmente una plantilla de elementos sin usar el Asistente para exportar plantillas

En algunos casos es posible que quiera crear una plantilla de elementos manualmente desde cero.

1. Cree un proyecto y un elemento de proyecto.

1. Modifique el elemento de proyecto hasta que se pueda guardar como plantilla.

1. Modifique el archivo de código para indicar dónde debe aplicarse el reemplazo de parámetros, si se debe aplicar alguno. Para más información sobre el reemplazo de parámetros, consulte [Cómo: Sustituir parámetros en una plantilla](../ide/how-to-substitute-parameters-in-a-template.md).

1. Cree un archivo XML y guárdelo con la extensión de archivo .vstemplate en el mismo directorio del archivo de elemento de proyecto.

1. Edite el archivo XML .vstemplate para proporcionar los metadatos de la plantilla de elementos. Para obtener más información, vea [Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md) y el ejemplo de la sección anterior.

1. Guarde el archivo .vstemplate y ciérrelo.

1. En el Explorador de Windows, seleccione los archivos que quiera incluir en la plantilla, haga clic con el botón derecho en la selección y elija **Enviar a** > **Carpeta comprimida (en zip)**. Los archivos seleccionados se comprimen en un archivo .zip.

1. Copie el archivo .zip y péguelo en la ubicación de la plantilla de elementos del usuario. En Visual Studio 2017, el directorio predeterminado es %USERPROFILE%\Documentos\Visual Studio 2017\Templates\ItemTemplates. Para obtener más información, vea [Cómo: Localizar y organizar plantillas de proyecto y de elemento](../ide/how-to-locate-and-organize-project-and-item-templates.md).

## <a name="see-also"></a>Vea también

[Crear plantillas para proyectos y elementos en Visual Studio](../ide/creating-project-and-item-templates.md)  
[Cómo: Crear plantillas de elementos de varios archivos](../ide/how-to-create-multi-file-item-templates.md)  
[Referencia de esquema de plantilla de Visual Studio (Extensibilidad)](../extensibility/visual-studio-template-schema-reference.md)
