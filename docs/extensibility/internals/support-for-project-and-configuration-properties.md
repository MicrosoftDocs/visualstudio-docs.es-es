---
title: Compatibilidad con proyectos y propiedades de configuración | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: d2f61bce5b54dc877117af71b07dc0bfc1fdd8b9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/02/2019
ms.locfileid: "53893531"
---
# <a name="support-for-project-and-configuration-properties"></a>Compatibilidad con las propiedades de proyecto y configuración
El **propiedades** ventana en la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el entorno de desarrollo integrado (IDE) puede mostrar las propiedades de configuración y el proyecto. Puede proporcionar una página de propiedades para su propio tipo de proyecto para que el usuario puede establecer las propiedades de la aplicación.  
  
 Al seleccionar un nodo de proyecto en **el Explorador de soluciones** y, a continuación, haga clic en **propiedades** en el **proyecto** menú, puede abrir un cuadro de diálogo que incluye la configuración y el proyecto Propiedades. En [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] y [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]y el proyecto tipos derivados de estos idiomas, este cuadro de diálogo aparece como una página con pestañas en el [General, entorno, cuadro de diálogo Opciones](../../ide/reference/general-environment-options-dialog-box.md). Para obtener más información, consulte [no en la compilación: Tutorial: Exponer propiedades de configuración (C#) y proyectos](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e).  
  
 Managed Package Framework para proyectos (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema de proyectos. Puede encontrar el origen de las instrucciones de código y compilación en [MPF de proyectos: Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
## <a name="persistence-of-project-and-configuration-properties"></a>Persistencia de proyecto y las propiedades de configuración  
 Propiedades de configuración y el proyecto se almacenan en un archivo de proyecto que tenga cualquier extensión de nombre de archivo asociado con el tipo de proyecto, por ejemplo, .csproj, .vbproj y .myproj. Proyectos de lenguaje suelen usan un archivo de plantilla para generar el archivo de proyecto. Sin embargo, hay realmente de varias maneras para asociar tipos de proyectos y plantillas. Para obtener más información, consulte [descripción del directorio de plantilla (. Archivos VSDir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).  
  
 Propiedades de configuración y los proyectos se crean agregando elementos al archivo de plantilla. Estas propiedades, a continuación, están disponibles para todos los proyectos creados con el tipo de proyecto que usa esta plantilla. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] proyectos y la MPFProj ambos usan la [no en la compilación: Información general sobre MSBuild](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) esquema para archivos de plantilla. Estos archivos tienen una sección PropertyGroup para cada configuración. Propiedades de los proyectos normalmente se conservan en la primera sección PropertyGroup, que tiene un argumento de la configuración establecida en una cadena nula.  
  
 El código siguiente muestra el inicio de un archivo de proyecto de MSBuild básico.  
  
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
>  Un proyecto puede optimizar la persistencia por conservar los valores de propiedad única que difieren de los valores predeterminados.  
  
## <a name="support-for-project-and-configuration-properties"></a>Compatibilidad con las propiedades de proyecto y configuración  
 La `Microsoft.VisualStudio.Package.SettingsPage` clase implementa las páginas de propiedades de configuración y el proyecto. La implementación predeterminada de `SettingsPage` ofrece propiedades públicas a un usuario en una cuadrícula de propiedades genéricas. El `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` método selecciona las clases derivadas de `SettingsPage` para las cuadrículas de propiedades del proyecto. El `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` método selecciona las clases derivadas de `SettingsPage` para las cuadrículas de propiedades de configuración. El tipo de proyecto debe invalidar estos métodos para seleccionar las páginas de propiedades adecuado.  
  
 El `SettingsPage` clase y el `Microsoft.VisualStudio.Package.ProjectNode` estos métodos para conservar las propiedades del proyecto y la configuración de la oferta de clase:  
  
- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty` y `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` conservar las propiedades del proyecto.  
  
- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty` y `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` conservar las propiedades de configuración.  
  
  > [!NOTE]
  >  Las implementaciones de la `Microsoft.VisualStudio.Package.SettingsPage` y `Microsoft.VisualStudio.Package.ProjectNode` clases utilizan el `Microsoft.Build.BuildEngine` métodos (MSBuild) para obtener y establecer propiedades del proyecto y la configuración en el archivo de proyecto.  
  
  La clase se deriva de `SettingsPage` debe implementar `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` y `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` para conservar las propiedades de configuración del proyecto o del archivo del proyecto.  
  
## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute y ruta de acceso del registro  
 Las clases derivadas de `SettingsPage` están diseñados para compartirse entre VSPackages. Para hacer posible que un VSPackage crear una clase derivada de `SettingsPage`, agregue un `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` a una clase derivada de `Microsoft.VisualStudio.Shell.Package`.  
  
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]  
  
 El VSPackage al que está asociado el atributo no es significativo. Cuando se registra un VSPackage con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], se registra el Id. de clase (CLSID) de cualquier objeto que se puede crear para que una llamada a <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> puede crearla.  
  
 La ruta de acceso del registro de un objeto que se puede crear se determina mediante la combinación <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>, la palabra, CLSID y el guid del tipo de objeto. Si `MyProjectPropertyPage` clase tiene un guid de {3c693da2-5bca-49b3-bd95-ffe0a39dd723} y el UserRegistryRoot HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\8.0Exp, entonces la ruta de acceso del registro sería HKEY_CURRENT_USER\Software\Microsoft\VisualStudio \8.0Exp\CLSID\\{3c693da2-5bca-49b3-bd95-ffe0a39dd723}.  
  
## <a name="project-and-configuration-property-attributes-and-layout"></a>Atributos de propiedad de configuración y el proyecto y diseño  
 El <xref:System.ComponentModel.CategoryAttribute>, <xref:System.ComponentModel.DisplayNameAttribute>, y <xref:System.ComponentModel.DescriptionAttribute> atributos determinan el diseño, el etiquetado y la descripción de las propiedades de configuración y el proyecto en una página de propiedades genéricas. Estos atributos determinar la categoría, nombre para mostrar y descripción de la opción, respectivamente.  
  
> [!NOTE]
>  Atributos equivalentes, SRCategory, LocDisplayName y SRDescription, use los recursos de cadena para la localización y se definen en [MPF de proyectos: Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).  
  
 Observe el fragmento de código siguiente:  
  
 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]  
  
 El `MyConfigProp` propiedad configuración aparece en la página de propiedades de configuración como **mi propiedad Config** en la categoría, **My Category**. Si se selecciona la opción, la descripción, **mi descripción**, aparece en el panel de descripción.  
  
## <a name="see-also"></a>Vea también  
 [Agregar y quitar páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)   
 [Proyectos](../../extensibility/internals/projects.md)   
 [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
