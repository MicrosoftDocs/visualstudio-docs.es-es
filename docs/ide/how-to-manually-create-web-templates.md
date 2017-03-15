---
title: "C&#243;mo: Crear plantillas web manualmente | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plantillas de proyecto [Visual Studio], Web"
  - "plantillas [Visual Studio], Web"
  - "plantillas de Visual Studio, Web"
  - "plantillas web [Visual Studio]"
ms.assetid: 731c4027-a152-48c5-bfc4-93490bf1949f
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 17
---
# C&#243;mo: Crear plantillas web manualmente
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

El proceso de creación de una plantilla web es ligeramente diferente al de crear otros tipos de plantillas.  Debido a que las plantillas de los proyectos web aparecen en el cuadro de diálogo **Agregar nuevo sitio web** y a que los elementos de proyectos web se clasifican por lenguaje de programación, el archivo .vstemplate debe especificar que se trata de una plantilla web e identificar el lenguaje de programación.  
  
> [!NOTE]
>  Las plantillas web deben contener un archivo .webproj vacío que se especifica mediante el atributo `File` del elemento `Project`.  Aunque los proyectos web no requieren archivos de proyecto, este archivo es necesario para el buen funcionamiento de las plantillas web.  
  
### Para crear manualmente una plantilla Web  
  
1.  Cree un proyecto web.  
  
2.  Modifique o elimine los archivos del proyecto o agréguele nuevos archivos.  
  
3.  Cree un archivo XML y guárdelo con la extensión .vstemplate en el mismo directorio que el proyecto.  No lo agregue al proyecto en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
4.  Cree el archivo XML con extensión .vstemplate para proporcionar los metadatos de la plantilla de proyecto.  Para obtener más información, vea el ejemplo de la siguiente sección.  
  
5.  Busque el elemento `ProjectType` en el archivo .vstemplate y establezca el valor de texto en `Web`.  
  
6.  Tras el elemento `ProjectType`, agregue un elemento `ProjectSubType` y establezca el valor de texto en el lenguaje de programación de la plantilla.  El lenguaje de programación puede ser uno de los siguientes valores:  
  
    -   CSharp  
  
    -   VisualBasic  
  
     Por ejemplo:  
  
    ```  
    <TemplateData>  
        ...  
        <ProjectType>Web</ProjectType>  
        <ProjectSubType>CSharp</ProjectSubType>  
        ...  
    </TemplateData>  
    ```  
  
7.  Seleccione los archivos de la plantilla \(también el archivo .vstemplate\), haga clic con el botón secundario en la selección, haga clic en **Enviar a** y, a continuación, en **Carpeta comprimida \(en zip\)**.  Los archivos se comprimen en un archivo .zip.  
  
8.  Coloque el archivo de plantilla .zip en el directorio de plantillas de proyecto de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  de forma predeterminada, este directorio es \\My Documents\\Visual Studio *Versión*\\My Exported Templates \\.  
  
## Ejemplo  
 En el ejemplo siguiente se muestra un archivo .vstemplate básico para una plantilla de proyecto web.  
  
```  
<VSTemplate Version="2.0.0" Type="Project"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">>  
    <TemplateData>  
        <Name>MyWebProjecStarterKit</Name>  
        <Description>A simple Web template</Description>  
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
  
## Vea también  
 [Crear plantillas de proyecto y de elemento personalizadas](../ide/creating-project-and-item-templates.md)   
 [Referencia de esquema de plantillas de Visual Studio](../extensibility/visual-studio-template-schema-reference.md)