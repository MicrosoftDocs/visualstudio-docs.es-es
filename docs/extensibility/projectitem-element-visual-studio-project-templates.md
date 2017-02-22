---
title: "ProjectItem (Elemento, Plantillas de proyecto de Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProjectItem"
helpviewer_keywords: 
  - "<ProjectItem> (elemento) [plantillas de proyecto de Visual Studio]"
  - "ProjectItem (elemento) [plantillas de proyecto de Visual Studio]"
ms.assetid: 82879fbe-7756-42cd-9a07-c10edf5b4673
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# ProjectItem (Elemento, Plantillas de proyecto de Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Especifica un archivo que se incluye en la plantilla de proyecto.  
  
> [!NOTE]
>  El elemento `ProjectItem` acepta atributos diferentes que dependen de si la plantilla es para un proyecto o un elemento.  En este tema se explica el elemento `ProjectItem` para las plantillas de proyecto.  Para obtener una explicación del elemento `ProjectItem` para las plantillas de elementos, vea [ProjectItem \(Elemento, Plantillas de elementos de Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md).  
  
## Sintaxis  
  
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
  
## Atributos y elementos  
 Las siguientes secciones describen atributos, elementos secundarios y elementos primarios.  
  
### Atributos  
  
|Atributo|Descripción|  
|--------------|-----------------|  
|`TargetFileName`|Atributo opcional.<br /><br /> Especifica el nombre y la ruta de acceso del elemento de proyecto al crear un proyecto a partir de la plantilla.  Este atributo resulta de gran utilidad si se desea crear una estructura de directorios distinta de la contenida en el archivo .zip de la plantilla o si se desea utilizar el reemplazo de parámetros para crear un nombre de elemento.|  
|`ReplaceParameters`|Atributo opcional.<br /><br /> Un valor booleano que especifica si el elemento tiene valores de parámetro que se deben reemplazar cuando se crea un proyecto a partir de la plantilla.  El valor predeterminado es `false`.|  
|`OpenInEditor`|Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento se debe abrir en su editor correspondiente en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] al crear un proyecto a partir de la plantilla.<br /><br /> Los atributos `OpenInWebBrowser` y `OpenInHelpBrowser` se omiten en un elemento cuyo valor de `OpenInEditor` es `true`.<br /><br /> El valor predeterminado es `false`.|  
|`OpenInWebBrowser`|Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento se debe abrir en el explorador web al crear un proyecto a partir de la plantilla.<br /><br /> En el Explorador Web solo se abrirán los archivos HTML y de texto locales con respecto al proyecto.  Las direcciones URL externas no se pueden abrir con este atributo.<br /><br /> El valor predeterminado es `false`.|  
|`OpenInHelpBrowser`|Atributo opcional.<br /><br /> Valor booleano que especifica si el elemento se debe abrir en el visor de Ayuda al crear un proyecto a partir de la plantilla.<br /><br /> Sólo se abrirán en el explorador web los archivos HTML y de texto locales con respecto al proyecto.  Las direcciones URL externas no se pueden abrir con este atributo.<br /><br /> El valor predeterminado es `false`.|  
|`OpenOrder`|Atributo opcional.<br /><br /> Especifica un valor numérico que representa el orden en que se abrirán los elementos en sus editores respectivos.  Todos los valores deben ser múltiplos de 10.  Los elementos con los valores más altos `OpenOrder` se abra primero.|  
  
### Elementos secundarios  
 Ninguno.  
  
### Elementos primarios  
  
|Elemento|Descripción|  
|--------------|-----------------|  
|[Proyecto](../extensibility/project-element-visual-studio-templates.md)|Especifica los archivos o directorios que se agregarán al proyecto.|  
  
## Valor de texto  
 Se requiere un valor de texto.  
  
 `string` que representa el nombre o la ruta de acceso a un archivo en el archivo .zip de la plantilla.  
  
## Comentarios  
 `ProjectItem` es un elemento secundario opcional de `Project`.  
  
 El atributo `TargetFileName` se puede utilizar para crear una estructura de directorios diferente a partir de la estructura de directorios del archivo .zip de la plantilla.  Por ejemplo, si el archivo `MyFile.vb` se encuentra en el directorio raíz del archivo .zip de la plantilla pero desea colocarlo en un directorio denominado `CustomFiles` en todos los proyectos creados a partir de la plantilla, deberá utilizar el siguiente código XML:  
  
```  
<ProjectItem TargetFileName="CustomFiles\MyFile.vb">MyFile.vb</ProjectItem>  
```  
  
 El atributo `TargetFileName` también se puede utilizar para cambiar el nombre de archivos que contienen caracteres internacionales en sus nombres de archivo.  Por ejemplo, un archivo .zip de la plantilla no puede contener nombres de archivo con caracteres Unicode, por tanto hay que cambiar el nombre del archivo antes de ser comprimido en un archivo .zip.  El atributo `TargetFileName` se puede utilizar para volver a establecer el nombre de archivo en el nombre de archivo Unicode original.  
  
 El atributo `TargetFileName` también se puede utilizar para cambiar el nombre de los archivos con parámetros.  El procedimiento siguiente explica cómo cambiar el nombre del archivo `MyFile.vb`, que se encuentra en el directorio raíz del archivo .zip de plantilla, a un nombre de archivo basado en el nombre del proyecto.  
  
### Para cambiar nombres de archivo con parámetros  
  
1.  Utilice el XML siguiente en el archivo .vstemplate:  
  
    ```  
    <ProjectItem TargetFileName="$safeprojectname$.vb">MyFile.vb</ProjectItem>  
    ```  
  
2.  Abra el archivo de proyecto \(.vbproj para un proyecto de [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) en un editor de texto o [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
3.  Busque la línea del archivo de proyecto que parece similar al XML siguiente:  
  
    ```  
    <Compile Include="MyFile.vb">  
    ```  
  
4.  Reemplace la línea de código con el XML siguiente:  
  
    ```  
    <Compile Include="$safeprojectname$.vb">  
    ```  
  
     Cuando se cree un proyecto a partir de esta plantilla, el nombre del archivo se basará en el nombre especificado por el usuario en el cuadro de diálogo **Nuevo proyecto**, tras quitar todos los caracteres no seguros y los espacios.  Para obtener más información, vea [Parámetros de plantilla](../ide/template-parameters.md).  
  
## Ejemplo  
 En el ejemplo siguiente se muestran los metadatos de una plantilla de proyecto de una aplicación de [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
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
  
## Vea también  
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Parámetros de plantilla](../ide/template-parameters.md)   
 [ProjectItem \(Elemento, Plantillas de elementos de Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)