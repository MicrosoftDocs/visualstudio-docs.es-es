---
title: Soporte para Propiedades de Proyecto y Configuración (Project and Configuration Properties) Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- project properties, supporting with Visual Studio SDK
- configuration properties, supporting with Visual Studio SDK
ms.assetid: 9fcfaa0f-7b41-4b68-82ec-7a151dca5d7e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c21d552e26add3a5159febd666c1f60573697535
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704898"
---
# <a name="support-for-project-and-configuration-properties"></a>Compatibilidad con las propiedades de proyecto y configuración
La **Properties** ventana Propiedades [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] del entorno de desarrollo integrado (IDE) puede mostrar las propiedades de proyecto y configuración. Puede proporcionar una página de propiedades para su propio tipo de proyecto para que el usuario pueda establecer propiedades para la aplicación.

 Al seleccionar un nodo de proyecto en el **Explorador** de soluciones y, a continuación, hacer clic en **Propiedades** en el menú **Proyecto,** puede abrir un cuadro de diálogo que incluya las propiedades de proyecto y configuración. En [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)]y , y tipos de proyecto derivados de estos idiomas, este cuadro de diálogo aparece como una página con fichas en el cuadro de [diálogo General, Entorno, Opciones](../../ide/reference/general-environment-options-dialog-box.md). Para obtener más información, vea [No en compilación: Tutorial: exponer](https://msdn.microsoft.com/library/d850d63b-25e2-4505-9f3d-eb038d7c1d0e)propiedades de proyecto y configuración (C- ) .

 Managed Package Framework for Projects (MPFProj) proporciona clases auxiliares para crear y administrar un nuevo sistema de proyectos. Puede encontrar el código fuente y las instrucciones de compilación en [MPF for Projects - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

## <a name="persistence-of-project-and-configuration-properties"></a>Persistencia de las propiedades de proyecto y configuración
 Las propiedades de proyecto y configuración se conservan en un archivo de proyecto que tiene cualquier extensión de nombre de archivo asociada al tipo de proyecto, por ejemplo, .csproj, .vbproj y .myproj. Los proyectos de lenguaje suelen usar un archivo de plantilla para generar el archivo de proyecto. Sin embargo, en realidad hay varias maneras de asociar tipos de proyecto y plantillas. Para obtener más información, consulte Descripción del directorio de [plantillas (. Vsdir) Archivos](../../extensibility/internals/template-directory-description-dot-vsdir-files.md).

 Las propiedades de proyecto y configuración se crean agregando elementos al archivo de plantilla. Estas propiedades están disponibles para cualquier proyecto creado mediante el tipo de proyecto que usa esta plantilla. [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)]proyectos y MPFProj usan el esquema [Not in Build: MSBuild Overview](/previous-versions/visualstudio/visual-studio-2008/ms171452(v=vs.90)) para los archivos de plantilla. Estos archivos tienen una sección PropertyGroup para cada configuración. Las propiedades de los proyectos normalmente se conservan en la primera sección PropertyGroup, que tiene un argumento Configuration establecido en una cadena nula.

 El código siguiente muestra el inicio de un archivo de proyecto básico de MSBuild.

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

 En este archivo `<Name>` `<SchemaVersion>` de proyecto y `<Optimize>` son propiedades de proyecto y es una propiedad de configuración.

 Es responsabilidad del proyecto conservar las propiedades de proyecto y configuración del archivo de proyecto.

> [!NOTE]
> Un proyecto puede optimizar la persistencia conservando solo los valores de propiedad que difieren de sus valores predeterminados.

## <a name="support-for-project-and-configuration-properties"></a>Compatibilidad con las propiedades de proyecto y configuración
 La `Microsoft.VisualStudio.Package.SettingsPage` clase implementa páginas de propiedades de proyecto y configuración. La implementación `SettingsPage` predeterminada de ofrece propiedades públicas a un usuario en una cuadrícula de propiedades genéricas. El `Microsoft.VisualStudio.Package.HierarchyNode.GetPropertyPageGuids` método selecciona las `SettingsPage` clases derivadas de las cuadrículas de propiedades del proyecto. El `Microsoft.VisualStudio.Package.ProjectNode.GetConfigPropertyPageGuids` método selecciona las `SettingsPage` clases derivadas de las cuadrículas de propiedades de configuración. El tipo de proyecto debe invalidar estos métodos para seleccionar las páginas de propiedades adecuadas.

 La `SettingsPage` clase `Microsoft.VisualStudio.Package.ProjectNode` y la clase ofrecen estos métodos para conservar las propiedades de proyecto y configuración:

- `Microsoft.VisualStudio.Package.ProjectNode.GetProjectProperty`y `Microsoft.VisualStudio.Package.ProjectNode.SetProjectProperty` persista las propiedades del proyecto.

- `Microsoft.VisualStudio.Package.SettingsPage.GetConfigProperty`y `Microsoft.VisualStudio.Package.SettingsPage.SetConfigProperty` conservar las propiedades de configuración.

  > [!NOTE]
  > Las implementaciones `Microsoft.VisualStudio.Package.SettingsPage` de `Microsoft.VisualStudio.Package.ProjectNode` las `Microsoft.Build.BuildEngine` clases y usan los métodos (MSBuild) para obtener y establecer las propiedades de proyecto y configuración desde el archivo de proyecto.

  La clase de `SettingsPage` la `Microsoft.VisualStudio.Package.SettingsPage.ApplyChanges` `Microsoft.VisualStudio.Package.SettingsPage.BindProperties` que deriva debe implementar y conservar las propiedades de proyecto o configuración del archivo de proyecto.

## <a name="provideobjectattribute-and-registry-path"></a>ProvideObjectAttribute y ruta del registro
 Las clases `SettingsPage` derivadas de están diseñadas para compartirse entre VSPackages. Para que sea posible que un VSPackage `SettingsPage`cree una `Microsoft.VisualStudio.Shell.ProvideObjectAttribute` clase derivada de `Microsoft.VisualStudio.Shell.Package`, agregue a una clase derivada de .

 [!code-csharp[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_1.cs)]
 [!code-vb[VSSDKSupportProjectConfigurationProperties#1](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_1.vb)]

 El VSPackage al que está asociado el atributo no es importante. Cuando se registra un [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]VSPackage con , el identificador de clase (CLSID) de <xref:Microsoft.VisualStudio.Shell.Interop.ILocalRegistry.CreateInstance%2A> cualquier objeto que se puede crear se registra para que una llamada a puede crearlo.

 La ruta de acceso del Registro de <xref:Microsoft.VisualStudio.Shell.Package.UserRegistryRoot%2A>un objeto que se puede crear se determina combinando , la palabra, CLSID y el guid del tipo de objeto. Si `MyProjectPropertyPage` la clase tiene un guid de .3c693da2-5bca-49b3-bd95-ffe0a39dd723 y el UserRegistryRoot es HKEY_CURRENT_USER, Software, Microsoft, VisualStudio, 8.0Exp, a continuación, la\\ruta de acceso del Registro sería HKEY_CURRENT_USER,Software, Microsoft, VisualStudio, 8.0Exp, CLSID, 3c693da2-5bca-49b3-bd95-ffe0a39dd723.

## <a name="project-and-configuration-property-attributes-and-layout"></a>Atributos y diseño de propiedades de proyecto y configuración
 Los <xref:System.ComponentModel.CategoryAttribute> <xref:System.ComponentModel.DisplayNameAttribute>atributos <xref:System.ComponentModel.DescriptionAttribute> , y , y determinan el diseño, el etiquetado y la descripción de las propiedades de proyecto y configuración en una página de propiedades genérica. Estos atributos determinan la categoría, el nombre para mostrar y la descripción de la opción, respectivamente.

> [!NOTE]
> Los atributos equivalentes, SRCategory, LocDisplayName y SRDescription, usan recursos de cadena para la localización y se definen en [MPF para Proyectos - Visual Studio 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Observe el fragmento de código siguiente:

 [!code-vb[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/VisualBasic/support-for-project-and-configuration-properties_2.vb)]
 [!code-csharp[VSSDKSupportProjectConfigurationProperties#2](../../extensibility/internals/codesnippet/CSharp/support-for-project-and-configuration-properties_2.cs)]

 La `MyConfigProp` propiedad de configuración aparece en la página de propiedades de configuración como **My Config Property** en la categoría My **Category**. Si la opción está seleccionada, la descripción, **Mi descripción**, aparece en el panel de descripción.

## <a name="see-also"></a>Vea también
- [Adición y eliminación de páginas de propiedades](../../extensibility/adding-and-removing-property-pages.md)
- [Proyectos](../../extensibility/internals/projects.md)
- [Archivos de descripción del directorio de plantilla (.Vsdir)](../../extensibility/internals/template-directory-description-dot-vsdir-files.md)
