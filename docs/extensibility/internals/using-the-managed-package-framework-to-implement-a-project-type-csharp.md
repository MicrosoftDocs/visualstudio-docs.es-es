---
title: Mediante Managed Package Framework para un tipo de proyecto (C#) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
caps.latest.revision: "20"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 16e1d301e5a3977f656c52f9c97eb43ee216075f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Uso de Managed Package Framework para implementar un tipo de proyecto (C#)
Managed Package Framework (MPF) proporciona clases de C# pueden utilizar o heredar para implementar sus propios tipos de proyecto. MPF implementa muchas de las interfaces de que Visual Studio espera un tipo de proyecto para proporcionar, queda libre para centrarse en la implementación de las indicaciones de su tipo de proyecto.  
  
## <a name="using-the-mpf-project-source-code"></a>Uso de código fuente del proyecto MPF  
 Managed Package Framework para proyectos (MPFProj) proporciona clases auxiliares para crear y administrar el nuevo sistema de proyectos. A diferencia de otras clases de MPF, las clases del proyecto no se incluyen en los ensamblados incluidos con Visual Studio. En su lugar, las clases del proyecto se proporcionan como código fuente en [MPF para proyectos 2013](http://mpfproj12.codeplex.com).  
  
 Para agregar este proyecto a la solución de VSPackage, haga lo siguiente:  
  
1.  Descargar los archivos de MPFProj en *MPFProjectDir*.  
  
2.  En el *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, cambie el bloque siguiente:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Cree un proyecto de VSPackage.  
  
2.  Descargue el proyecto de VSPackage.  
  
3.  Edite el archivo .csproj de VSPackage agregando el siguiente bloque antes que el otro `<Import>` bloques:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Guarde el proyecto.  
  
2.  Cierre y vuelva a abrir la solución de VSPackage.  
  
3.  Vuelva a abrir el proyecto de VSPackage. Debería ver un directorio denominado ProjectBase.  
  
4.  Agregue la siguiente referencia al proyecto de VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Compile el proyecto.  
  
## <a name="hierarchy-classes"></a>Clases de jerarquía  
 En la tabla siguiente se resume las clases en el MPFProj que admiten jerarquías de proyecto. Para obtener más información, consulte [jerarquías y selección](../../extensibility/internals/hierarchies-and-selection.md).  
  
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
  
## <a name="document-handling-classes"></a>Clases de control de documento  
 En la tabla siguiente se enumera las clases de MPF que admiten el control de documento. Para obtener más información, consulte [abrir y guardar elementos de proyecto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nombre de la clase|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Configuración y las clases de salida  
 En la tabla siguiente muestra las clases de MPF que permiten tipos de proyecto admite varias configuraciones, como debug y release y colecciones de salida del proyecto. Para obtener más información, consulte [administrar opciones de configuración](../../extensibility/internals/managing-configuration-options.md).  
  
|Nombre de la clase|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Clases de compatibilidad de la automatización  
 En la tabla siguiente se enumera las clases de MPF que admiten la automatización para que los usuarios de su tipo de proyecto pueden escribir complementos.  
  
|Nombre de la clase|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Clases de propiedades  
 La siguiente tabla se enumeran las clases de MPF que permiten tipos de proyecto agregan propiedades que los usuarios pueden examinar y modificar en un explorador de propiedades.  
  
|Nombre de la clase|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|