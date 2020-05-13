---
title: Elemento ProjectItem (Plantillas de proyecto de Visual Studio) Microsoft Docs
ms.date: 11/04/2016
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem
helpviewer_keywords:
- ProjectItem element [Visual Studio project templates]
- <ProjectItem> element [Visual Studio project templates]
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 11052d8e585f1d06f6d787402001cfbbe2b6810f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80701847"
---
# <a name="projectitem-element-visual-studio-project-templates"></a>Elemento ProjectItem (plantillas de proyecto de Visual Studio)
Especifica un archivo que se incluye en la plantilla de proyecto.

> [!NOTE]
> El `ProjectItem` elemento acepta atributos diferentes dependiendo de si la plantilla es para un proyecto o un elemento. En este `ProjectItem` tema se explica el elemento para las plantillas de proyecto. Para obtener una `ProjectItem` explicación del elemento para las plantillas de elemento, vea [ProjectItem Element (Plantillas](../extensibility/projectitem-element-visual-studio-item-templates.md)de elemento de Visual Studio) .

 \<VSTemplate \<> TemplateContent \< \<> ProjectItem>>

## <a name="syntax"></a>Sintaxis

```
<ProjectItem
    TargetFileName="TargetFileName.ext"
    ReplaceParameters="true/false"
    OpenInEditor="true/false"
    OpenInWebBrowser="true/false"
    OpenInHelpBrowser="true/false"
    OpenOrder="Value">
        FileName.ext
</ProjectItem>
```

## <a name="attributes-and-elements"></a>Atributos y elementos
 En las siguientes secciones se describen los atributos, los elementos secundarios y los elementos primarios.

### <a name="attributes"></a>Atributos

| Atributo | Descripción |
|---------------------| - |
| `TargetFileName` | Atributo opcional.<br /><br /> Especifica el nombre y la ruta de acceso del elemento de proyecto cuando se crea un proyecto a partir de la plantilla. Este atributo es útil para crear una estructura de directorios diferente de la estructura de directorios en el archivo *.zip* de plantilla o para usar el reemplazo de parámetros para crear un nombre de elemento. |
| `ReplaceParameters` | Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento tiene valores de parámetro que se deben reemplazar cuando se crea un proyecto a partir de la plantilla. El valor predeterminado es `false`. |
| `OpenInEditor` | Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento debe [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] abrirse en su editor respectivo cuando se crea un proyecto a partir de la plantilla.<br /><br /> Los `OpenInWebBrowser` `OpenInHelpBrowser` atributos y se omiten en un elemento con un `OpenInEditor` valor de `true`.<br /><br /> El valor predeterminado es `false`. |
| `OpenInWebBrowser` | Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento debe abrirse el explorador web cuando se crea un proyecto a partir de la plantilla.<br /><br /> Solo los archivos HTML y los archivos de texto que son locales para el proyecto se pueden abrir en el explorador web. Las direcciones URL externas no se pueden abrir con este atributo.<br /><br /> El valor predeterminado es `false`. |
| `OpenInHelpBrowser` | Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento se debe abrir en el visor de ayuda cuando se crea un proyecto a partir de la plantilla.<br /><br /> Solo los archivos HTML y los archivos de texto que son locales para el proyecto se pueden abrir en el explorador de ayuda. Las direcciones URL externas no se pueden abrir con este atributo.<br /><br /> El valor predeterminado es `false`. |
| `OpenOrder` | Atributo opcional.<br /><br /> Especifica un valor numérico que representa el orden en que se abrirán los elementos en sus respectivos editores. Todos los valores deben ser múltiplos de 10. Los elementos con valores más altos `OpenOrder` se abren primero. |

### <a name="child-elements"></a>Elementos secundarios
 Ninguno.

### <a name="parent-elements"></a>Elementos primarios

|Elemento|Descripción|
|-------------|-----------------|
|[Project](../extensibility/project-element-visual-studio-templates.md)|Especifica los archivos o directorios que se van a agregar al proyecto.|

## <a name="text-value"></a>Valor de texto
 Se requiere un valor de texto.

 A `string` que representa el nombre o la ruta de acceso a un archivo en el archivo *.zip* de plantilla.

## <a name="remarks"></a>Observaciones
 `ProjectItem`es un hijo `Project`opcional de .

 El `TargetFileName` atributo se puede utilizar para crear una estructura de directorios diferente de la estructura de directorios en el archivo *.zip* de plantilla. Por ejemplo, si el archivo *MyFile.vb* existe en la raíz del archivo *.zip* de plantilla, pero desea que el archivo se coloque en un directorio denominado *CustomFiles* en todos los proyectos creados a partir de la plantilla, usaría el siguiente XML:

```xml
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>
```

 El `TargetFileName` atributo también se puede utilizar para cambiar el nombre de los archivos que contienen caracteres internacionales en sus nombres de archivo. Por ejemplo, un archivo *.zip* de plantilla no puede contener nombres de archivo con caracteres Unicode, por lo que se debe cambiar el nombre del archivo antes de que se pueda comprimir en un archivo *.zip.* El `TargetFileName` atributo se puede utilizar para volver a establecer el nombre de archivo en el nombre de archivo Unicode original.

 El `TargetFileName` atributo también se puede utilizar para cambiar el nombre de los archivos con parámetros. El siguiente procedimiento explica cómo cambiar el nombre del archivo *MyFile.vb*, que existe en el directorio raíz del archivo *.zip* de plantilla, a un nombre de archivo basado en el nombre del proyecto.

### <a name="to-rename-files-with-parameters"></a>Para cambiar el nombre de los archivos con parámetros

1. Utilice el siguiente XML en el archivo *.vstemplate:*

   ```xml
   <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>
   ```

2. Abra el archivo de proyecto (*.vbproj* para un [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] proyecto) en un editor de texto o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

3. Busque la línea en el archivo de proyecto que sea similar al siguiente XML:

   ```xml
   <Compile Include="MyFile.vb">
   ```

4. Reemplace la línea de código por el siguiente XML:

   ```xml
   <Compile Include="$safeprojectname$.vb">
   ```

    Cuando se crea un proyecto a partir de esta plantilla, el nombre de archivo se basará en el nombre que el usuario ha especificado en el cuadro de diálogo **Nuevo proyecto,** con todos los caracteres y espacios no seguros eliminados. Para obtener más información, consulte [Parámetros](../ide/template-parameters.md)de plantilla .

## <a name="example"></a>Ejemplo
 En el ejemplo siguiente se muestran [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] los metadatos de una plantilla de proyecto para una aplicación.

```
<VSTemplate Type="Project" Version="3.0.0"
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">
    <TemplateData>
        <Name>My template</Name>
        <Description>A basic starter kit</Description>
        <Icon>TemplateIcon.ico</Icon>
        <ProjectType>CSharp</ProjectType>
    </TemplateData>
    <TemplateContent>
        <Project File="MyStarterKit.csproj">
            <ProjectItem ReplaceParameters="true">Form1.cs<ProjectItem>
            <ProjectItem>Form1.Designer.cs</ProjectItem>
            <ProjectItem>Program.cs</ProjectItem>
            <ProjectItem>Properties\AssemblyInfo.cs</ProjectItem>
            <ProjectItem>Properties\Resources.resx</ProjectItem>
            <ProjectItem>Properties\Resources.Designer.cs</ProjectItem>
            <ProjectItem>Properties\Settings.settings</ProjectItem>
            <ProjectItem>Properties\Settings.Designer.cs</ProjectItem>
        </Project>
    </TemplateContent>
</VSTemplate>
```

## <a name="see-also"></a>Vea también
- [Referencia de esquema de plantilla de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)
- [Crear plantillas de proyecto y elemento](../ide/creating-project-and-item-templates.md)
- [Parámetros de plantilla](../ide/template-parameters.md)
- [ProjectItem (Elemento, Plantillas de elementos de Visual Studio)](../extensibility/projectitem-element-visual-studio-item-templates.md)
