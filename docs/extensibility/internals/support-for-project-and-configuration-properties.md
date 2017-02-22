---
title: "Soporte t&#233;cnico para el proyecto y propiedades de configuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "propiedades del proyecto, compatibilidad con el SDK de Visual Studio"
  - "propiedades de configuración, suppporting con el SDK de Visual Studio"
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
caps.latest.revision: 25
caps.handback.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
---
# Soporte t&#233;cnico para el proyecto y propiedades de configuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

El **propiedades** ventana en el [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado \(IDE\) puede mostrar las propiedades de proyecto y la configuración. Puede proporcionar una página de propiedades para el tipo de proyecto para que el usuario puede establecer propiedades de la aplicación.  
  
 Al seleccionar un nodo de proyecto en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades** en el **proyecto** menú, puede abrir un cuadro de diálogo que incluye las propiedades de proyecto y la configuración. En [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)], y proyectos de tipos derivados de estos idiomas, este cuadro de diálogo aparece como una página con pestañas en el [General, Entorno, Opciones \(Cuadro de diálogo\)](../../ide/reference/general-environment-options-dialog-box.md). Para obtener más información, consulte [no en la compilación: Tutorial: exponer proyecto y propiedades de configuración \(C\#\)](http://msdn.microsoft.com/es-es/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Managed Package Framework para proyectos \(MPFProj\) proporciona clases auxiliares para crear y administrar el nuevo sistema de proyectos. Puede encontrar el origen de instrucciones de código y compilación en [MPF de proyectos: Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
## Persistencia de proyecto y propiedades de configuración  
 Propiedades de proyecto y la configuración se conservan en un archivo de proyecto que tiene una extensión de nombre de archivo asociado con el tipo de proyecto, por ejemplo, .csproj, .vbproj y .myproj. Proyectos de lenguaje normalmente utilizan un archivo de plantilla para generar el archivo de proyecto. Sin embargo, existen realmente de varias maneras para asociar tipos de proyectos y plantillas. Para obtener más información, consulte [NIB: plantillas de Visual Studio](http://msdn.microsoft.com/es-es/141fccaa-d68f-4155-822b-27f35dd94041) y [Descripción del directorio de plantilla \(. Archivos VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Propiedades de proyecto y la configuración se crean agregando elementos al archivo de plantilla. Estas propiedades, a continuación, están disponibles para cualquier proyecto creado utilizando el tipo de proyecto que usa esta plantilla.[!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyectos y la MPFProj ambos usan la [no en la compilación: información general sobre MSBuild](http://msdn.microsoft.com/es-es/b588fd73-a45b-4706-908f-cc131bccfbde) esquema de archivos de plantilla. Estos archivos tienen una sección PropertyGroup para cada configuración. Propiedades de proyectos normalmente se conservan en la primera sección PropertyGroup, que tiene un argumento de la configuración establecida en una cadena nula.  
  
 El código siguiente muestra el inicio de un archivo básico del proyecto de MSBuild.  
  
```  
<Project MSBuildVersion="2.0" DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <PropertyGroup>  
    <Configuration Condition=" '$(Configuration)' == '' ">Debug</Configuration>  
    <Name>SomeProjectSix</Name>  
    <SchemaVersion>2.0</SchemaVersion>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Debug' ">  
    <Optimize>false</Optimize>  
  </PropertyGroup>  
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">  
    <Optimize>true</Optimize>  
```  
  
 En este archivo de proyecto, `<Name>` y `<SchemaVersion>` son propiedades del proyecto, y `<Optimize>` es una propiedad de configuración.  
  
 Es responsabilidad del proyecto para conservar las propiedades del proyecto y la configuración del archivo del proyecto.  
  
> [!NOTE]
>  Un proyecto puede optimizar la persistencia al conservar los valores de propiedad única que difieren de los valores predeterminados.  
  
## Soporte técnico para el proyecto y propiedades de configuración  
 La `Microsoft.VisualStudio.Package.SettingsPage` clase implementa páginas de propiedades de proyecto y la configuración. La implementación predeterminada de `SettingsPage` ofrece propiedades públicas a un usuario en una cuadrícula de propiedades genérica. El `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` método selecciona las clases derivadas de `SettingsPage` de cuadrículas de propiedades del proyecto. El `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` método selecciona las clases derivadas de `SettingsPage` de cuadrículas de propiedades de configuración. El tipo de proyecto debe invalidar estos métodos para seleccionar las páginas de propiedades correspondiente.  
  
 La `SettingsPage` clase y la `Microsoft.VisualStudio.Package.ProjectNode` clase ofrecen estos métodos para conservar las propiedades del proyecto y la configuración:  
  
-   `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` y `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` conservar las propiedades del proyecto.  
  
-   `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` y `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` conservar propiedades de configuración.  
  
    > [!NOTE]
    >  Las implementaciones de la `Microsoft.VisualStudio.Package.SettingsPage` y `Microsoft.VisualStudio.Package.ProjectNode` clases utilizan el `Microsoft.Build.BuildEngine` métodos \(MSBuild\) para obtener y establecer propiedades de proyecto y la configuración del archivo de proyecto.  
  
 La clase se deriva de `SettingsPage` debe implementar `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` y `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` para conservar las propiedades de configuración del proyecto o del archivo del proyecto.  
  
## ProvideObjectAttribute y ruta de acceso del registro  
 Las clases derivadas de `SettingsPage` están diseñados para compartirse entre VSPackages. Para permitir que un VSPackage crear una clase derivada de `SettingsPage`, agregue un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` en una clase derivada de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-cs[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 El VSPackage al que está asociado el atributo no es significativo. Cuando se registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se registra el identificador de clase \(CLSID\) de cualquier objeto que se puede crear para que una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> puede crearlo.  
  
 La ruta de acceso del registro de un objeto que se puede crear se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra, CLSID y el guid del tipo de objeto. Si `MyProjectPropertyPage` clase tiene un guid de {3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723} y el UserRegistryRoot HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp, entonces la ruta de acceso del registro sería HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\8.0Exp\\CLSID\\{3c693da2\-5bca\-49b3\-bd95\-ffe0a39dd723}.  
  
## Atributos de la propiedad de configuración y el proyecto y diseño  
 El <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, y <xref:System.ComponentModel.DescriptionAttribute> atributos determinan el diseño, etiquetado y descripción de las propiedades de proyecto y la configuración en una página de propiedades genérica. Estos atributos determinar la categoría, nombre para mostrar y descripción de la opción, respectivamente.  
  
> [!NOTE]
>  Atributos equivalentes, SRCategory, LocDisplayName y SRDescription, utilice los recursos de cadena para la localización y se definen en [MPF de proyectos: Visual Studio 2013](http://mpfproj12.codeplex.com/).  
  
 Observe el fragmento de código siguiente:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-cs[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 El `MyConfigProp` propiedad configuración aparece en la página de propiedades de configuración como **mi propiedad Config** en la categoría **My Category**. Si la opción está seleccionada, la descripción, **mi descripción**, aparece en el panel Descripción.  
  
## Vea también  
 [No en la compilación: Tutorial: exponer propiedades de configuración \(C\#\) y de proyecto](http://msdn.microsoft.com/es-es/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)   
 [Agregar y quitar páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)   
 [Estado de VSPackage](../../misc/vspackage-state.md)   
 [Proyectos](../../extensibility/internals/projects.md)   
 [NIB: Plantillas de Visual Studio](http://msdn.microsoft.com/es-es/141fccaa-d68f-4155-822b-27f35dd94041)   
 [Descripción del directorio de plantilla \(. Archivos VSDir\)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)