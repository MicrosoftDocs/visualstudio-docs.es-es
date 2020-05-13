---
title: Uso de Managed Package Framework para un tipo de proyecto (C-) Microsoft Docs
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
ms.openlocfilehash: 7ca9dda0b699e0f70b0c945ab9ecfe9f9f4dcda6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704120"
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso de la plataforma de paquete administrado para implementar un tipo de proyecto (C#)
Managed Package Framework (MPF) proporciona clases de C- que puede usar o heredar para implementar sus propios tipos de proyecto. El MPF implementa muchas de las interfaces que Visual Studio espera que proporcione un tipo de proyecto, lo que le permite concentrarse en implementar los detalles del tipo de proyecto.

## <a name="using-the-mpf-project-source-code"></a>Uso del código fuente del proyecto MPF
 Managed Package Framework for Projects (MPFProj) proporciona clases auxiliares para crear y administrar un nuevo sistema de proyectos. A diferencia de otras clases en el MPF, las clases de proyecto no se incluyen en los ensamblados incluidos con Visual Studio. En su lugar, las clases de proyecto se proporcionan como código fuente en [MPF para Proyectos 2013.](https://github.com/tunnelvisionlabs/MPFProj10)

 Para agregar este proyecto a la solución de VSPackage, haga lo siguiente:

1. Descargue los archivos MPFProj en *MPFProjectDir*.

2. En el archivo *MPFProjectDir*, cambie el siguiente bloque:

```
<!-- Provide a default value for $(ProjectBasePath) -->
  <PropertyGroup>
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>
  </PropertyGroup>
```

1. Crear un proyecto de VSPackage.

2. Descargue el proyecto de VSPackage.

3. Edite el archivo .csproj de VSPackage agregando el siguiente bloque antes que los otros `<Import>` bloques:

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

3. Vuelva a abrir el proyecto VSPackage. Debería ver un nuevo directorio denominado ProjectBase.

4. Agregue la siguiente referencia al proyecto VSPackage:

     Microsoft.Build.Tasks.4.0

5. Compile el proyecto.

## <a name="hierarchy-classes"></a>Clases de jerarquía
 En la tabla siguiente se resumen las clases de MPFProj que admiten jerarquías de proyectos. Para obtener más información, consulte [Jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md).

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

## <a name="document-handling-classes"></a>Clases de gestión de documentos
 En la tabla siguiente se enumeran las clases del MPF que admiten el control de documentos. Para obtener más información, consulte Apertura y guardado de [elementos](../../extensibility/internals/opening-and-saving-project-items.md)de proyecto .

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.DocumentManager`|
|`Microsoft.VisualStudio.Package.FileDocumentManager`|

## <a name="configuration-and-output-classes"></a>Clases de configuración y salida
 En la tabla siguiente se enumeran las clases del MPF que permiten que los tipos de proyecto admitan varias configuraciones, como depuración y versión, y colecciones de salida del proyecto. Para obtener más información, consulte Administración de opciones de [configuración](../../extensibility/internals/managing-configuration-options.md).

|Nombre de la clase|
|----------------|
|`Microsoft.VisualStudio.Package.ConfigProvider`|
|`Microsoft.VisualStudio.Package.ProjectConfig`|
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|
|`Microsoft.VisualStudio.Package.OutputGroup`|
|`Microsoft.VisualStudio.Package.ProjectElement`|

## <a name="automation-support-classes"></a>Clases de automatización-soporte
 En la tabla siguiente se enumeran las clases del MPF que admiten la automatización para que los usuarios del tipo de proyecto puedan escribir complementos.

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
