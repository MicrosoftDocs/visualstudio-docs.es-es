---
title: "Par&#225;metros reemplazables"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "parámetros reemplazables [desarrollo de SharePoint en Visual Studio]"
  - "desarrollo de SharePoint en Visual Studio, parámetros reemplazables"
  - "desarrollo de SharePoint en Visual Studio, tokens"
  - "tokens [desarrollo de SharePoint en Visual Studio]"
ms.assetid: 3c46bbb1-0a98-495c-9fd1-dc57a6aedc11
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Par&#225;metros reemplazables
  Los parámetros reemplazables o *tokens* se pueden utilizar dentro de los archivos de proyecto para proporcionar los valores para los elementos de la solución de SharePoint cuyos valores reales no se conocen en tiempo de diseño.  Son similares en función de los tokens estándar de la plantilla de [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] .  Para obtener más información, vea [Parámetros de plantilla](../ide/template-parameters.md).  
  
## Formato de los tokens  
 Los tokens comienzan y finalizan con un carácter del signo de dólar \($\).  Cualquier token que se haya utilizado se reemplaza con valores reales cuando un proyecto se empaqueta en un archivo de paquete de solución \(.wsp\) de SharePoint en tiempo de implementación.  Por ejemplo, el token **$SharePoint.Package.Name$** se podría resolver como la cadena "Paquete de prueba de SharePoint".  
  
## Reglas de los tokens  
 Las reglas siguientes se aplican a los tokens:  
  
-   Los tokens se pueden especificar en cualquier parte en una línea.  
  
-   Los tokens no pueden abarcar varias líneas.  
  
-   El mismo token se puede especificar varias veces en la misma línea y en el mismo archivo.  
  
-   Los tokens diferentes se pueden especificar en la misma línea.  
  
 Los tokens que no siguen estas reglas se omiten sin proporcionar una advertencia o error.  
  
 El reemplazo de los tokens por valores de cadena se realiza inmediatamente después de la transformación de los manifiestos, por lo que se pueden usar tokens en las plantillas de manifiesto editadas por un usuario.  
  
### Resolución de nombres de tokens  
 En la mayoría de los casos, un token se resuelve como un valor concreto, independientemente de su ubicación.  Sin embargo, si el token está relacionado con un paquete o una característica, su valor dependerá de su ubicación.  Por ejemplo, si una característica está en el Paquete A, el token `$SharePoint.Package.Name$` se resolverá como "Paquete A". Si la misma característica está en el Paquete B, el token `$SharePoint.Package.Name$` se resolverá como "Paquete B".  
  
## Lista de tokens  
 En la tabla siguiente se enumeran los tokens disponibles.  
  
|Name|Descripción|  
|----------|-----------------|  
|$SharePoint.Project.FileName$|Nombre del archivo de proyecto contenedor; por ejemplo, "NuevoProy.csproj".|  
|$SharePoint.Project.FileNameWithoutExtension$|Nombre del archivo de proyecto contenedor, sin extensión.  Por ejemplo, "NuevoProy".|  
|$SharePoint.Project.AssemblyFullName$|Nombre para mostrar \(nombre seguro\) del ensamblado de salida del proyecto contenedor.|  
|$SharePoint.Project.AssemblyFileName$|Nombre del ensamblado de salida del proyecto contenedor.|  
|$SharePoint.Project.AssemblyFileNameWithoutExtension$|Nombre del ensamblado de salida del proyecto contenedor, sin extensión de nombre de archivo.|  
|$SharePoint.Project.AssemblyPublicKeyToken$|Token de clave pública del ensamblado de salida del proyecto contenedor, convertido en una cadena. \(16 caracteres en formato hexadecimal "x2"\).|  
|$SharePoint.Package.Name$|Nombre del paquete contenedor.|  
|$SharePoint.Package.FileName$|Nombre del archivo de definición del paquete contenedor.|  
|$SharePoint.Package.FileNameWithoutExtension$|Nombre \(sin extensión\) del archivo de definición del paquete contenedor.|  
|$SharePoint.Package.Id$|Identificador de SharePoint para el paquete contenedor.  Si se utiliza una característica en más de un paquete, este valor cambiará.|  
|$SharePoint.Feature.FileName$|Nombre del archivo de definición de la característica contenedora; por ejemplo, Feature1.feature.|  
|$SharePoint.Feature.FileNameWithoutExtension$|Nombre del archivo de definición de la característica, sin la extensión de nombre de archivo.|  
|$SharePoint.Feature.DeploymentPath$|Nombre de la carpeta que contiene la característica del paquete.  Este token equivale a la propiedad "Ruta de acceso de implementación" del Diseñador de características.  Un valor de ejemplo es "Project1\_Feature1".|  
|$SharePoint.Feature.Id$|Identificador de SharePoint para la característica contenedora.  Al igual que todos los tokens de nivel de característica, este token solo se puede usar en los archivos que se incluyen en un paquete a través de una característica; no se puede usar en los archivos que se agregan directamente a un paquete sin recurrir a una característica.|  
|$SharePoint.ProjectItem.Name$|Nombre del elemento de proyecto \(no su nombre de archivo\), obtenido de **ISharePointProjectItem.Name**.|  
|$SharePoint.Type.GUID.AssemblyQualifiedName$\<\>|El nombre completo del ensamblado del tipo que coincide con [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] de símbolos.  El formato de [!INCLUDE[TLA2#tla_guid](../sharepoint/includes/tla2sharptla-guid-md.md)] se escribe en minúsculas y corresponde al formato Guid.ToString \(“d”\) \(es decir, xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\).|  
|$SharePoint.Type.GUID.FullName$\<\>|Nombre completo del tipo que coincide con el GUID en el token.  El GUID se escribe en minúsculas y corresponde al formato Guid.ToString\("D"\) \(es decir, xxxxxxxx\-xxxx\-xxxx\-xxxx\-xxxxxxxxxxxx\).|  
  
## Agregar extensiones a la lista de extensiones de archivo de reemplazo de tokens  
 Aunque los tokens pueden usarse en teoría en cualquier archivo que pertenezca a un elemento de proyecto de SharePoint incluido en el paquete, de forma predeterminada [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] solo busca tokens en los archivos de paquete, los archivos de manifiesto y los archivos que tienen las extensiones siguientes:  
  
-   [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]  
  
-   ASCX  
  
-   ASPX  
  
-   Webpart  
  
-   DWP  
  
 Estas extensiones están definidas por el elemento de `<TokenReplacementFileExtensions>` en el archivo Microsoft.VisualStudio.SharePoint.targets, ubicado en… la carpeta\<\>de \\program files\\MSBuild\\Microsoft\\VisualStudio\\v11.0\\SharePointTools.  
  
 Puede, sin embargo, agregar extensiones de archivo adicionales a la lista.  Para ello, agregue un elemento de `<TokenReplacementFileExtensions>` a cualquier PropertyGroup del archivo de proyecto de SharePoint que se define antes \<de importación\> del archivo de destinos de SharePoint.  
  
> [!NOTE]  
>  Dado que los tokens se reemplazan una vez compilado un proyecto, no se deben agregar extensiones de archivo para tipos de archivo compilados, como .cs, .vb o .resx.  Los tokens se reemplazan únicamente en archivos que no están compilados.  
  
 Por ejemplo, para agregar las extensiones de nombre de archivo ".myextension" y ".yourextension" a la lista de extensiones de nombre de archivo de sustitución de tokens, se agregaría lo siguiente a un archivo .csproj:  
  
```  
<Project ToolsVersion="4.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Platform Condition=" '$(Platform)' == '' ">AnyCPU</Platform>  
.  
.  
.  
    <!-- Define the following property to add your extension to the list of token replacement file extensions.  -->  
<TokenReplacementFileExtensions>myextension;yourextension</TokenReplacementFileExtensions>  
</PropertyGroup>  
```  
  
 También se puede agregar la extensión directamente al archivo .targets.  Al hacerlo, sin embargo, se modifica la lista de extensiones de todos los proyectos de SharePoint empaquetados en el sistema local, no solo el suyo.  Esto puede ser conveniente si usted es el único desarrollador del sistema o si la mayoría de sus proyectos lo requiere.  Sin embargo, dado que es específico del sistema, este enfoque no es muy portátil y, por consiguiente, se recomienda agregar las extensiones al archivo de proyecto.  
  
## Vea también  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  