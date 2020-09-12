---
title: Usar Managed Package Framework para un tipo de proyecto (C#)
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: fca3f95780d548b4482c502f5b3eaa44005fd2e2
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2020
ms.locfileid: "90038652"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso de la plataforma de paquete administrado para implementar un tipo de proyecto (C#)
El marco de trabajo de paquetes administrados (MPF) proporciona clases de C# que puede usar o que heredan de para implementar sus propios tipos de proyecto. El MPF implementa muchas de las interfaces que Visual Studio espera que proporcione un tipo de proyecto, lo que le permite concentrarse en la implementación de los detalles del tipo de proyecto.

## <a name="using-the-mpf-project-source-code"></a>Usar el código fuente del proyecto MPF
 Managed Package Framework for Projects (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema del proyecto. A diferencia de otras clases del MPF, las clases de proyecto no se incluyen en los ensamblados que se incluyen con Visual Studio. En su lugar, las clases de proyecto se proporcionan como código fuente en [MPF para los proyectos 2013](https://github.com/tunnelvisionlabs/MPFProj10).

 Para agregar este proyecto a la solución de VSPackage, haga lo siguiente:

1. Descargue los archivos de MPFProj en *MPFProjectDir*.

2. En *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.File, cambie el siguiente bloque:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Cree un proyecto de VSPackage.

2. Descargue el proyecto de VSPackage.

3. Edite el archivo VSPackage. csproj agregando el siguiente bloque antes que los demás `<Import>` bloques:

```
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />
  <PropertyGroup>
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.
    <TargetRegistryRoot></TargetRegistryRoot>-->
    <RegisterOutputPackage>true</RegisterOutputPackage>
    <RegisterWithCodebase>true</RegisterWithCodebase>
  </PropertyGroup>
```

1. Guarde el proyecto.

2. Cierre y vuelva a abrir la solución VSPackage.

3. Vuelva a abrir el proyecto de VSPackage. Debería ver un nuevo directorio denominado ProjectBase.

4. Agregue la siguiente referencia al proyecto de VSPackage:

     Microsoft. Build. Tasks. 4.0

5. Compile el proyecto.

## <a name="hierarchy-classes"></a>Clases de jerarquía
 En la tabla siguiente se resumen las clases de MPFProj que admiten las jerarquías de proyecto. Para obtener más información, consulte [jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md).

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.HierarchyNode`|
|`Microsoft.VisualStudio.Package.ProjectNode`|
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|
|`Microsoft.VisualStudio.Package.FileNode`|
|`Microsoft.VisualStudio.Package.FolderNode`|
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|
|`Microsoft.VisualStudio.Package.ReferenceNode`|
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|
|`Microsoft.VisualStudio.Package.ComReferenceNode`|
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|
|`Microsoft.VisualStudio.Package.BuildDependency`|

## <a name="document-handling-classes"></a>Clases de control de documentos
 En la tabla siguiente se enumeran las clases de MPF que admiten el control de documentos. Para obtener más información, vea [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Clases de configuración y de salida
 En la tabla siguiente se enumeran las clases de MPF que permiten a los tipos de proyecto admitir varias configuraciones, como la depuración y liberación, y las colecciones de resultados del proyecto. Para obtener más información, vea [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Automation: clases compatibles
 En la tabla siguiente se enumeran las clases de MPF que admiten la automatización de modo que los usuarios del tipo de proyecto puedan escribir complementos.

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.Automation.OAProject`|
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|

## <a name="properties-classes"></a>Clases de propiedades
 En la tabla siguiente se enumeran las clases del MPF que permiten a los tipos de proyecto agregar propiedades que los usuarios pueden examinar y modificar en un explorador de propiedades.

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.LocalizableProperties`|
|`Microsoft.VisualStudio.Package.NodeProperties`|
|`Microsoft.VisualStudio.Package.FileNodeProperties`|
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
