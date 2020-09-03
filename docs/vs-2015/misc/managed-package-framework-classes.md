---
title: Clases de Managed Package Framework | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: jillfra
ms.openlocfilehash: 2e9fe1abb82d3d64232e3e5e2a6d117c1068aa1c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "74297703"
---
# <a name="managed-package-framework-classes"></a>Clases de Managed Package Framework
Las clases de Managed Package Framework (MPF) se pueden usar para crear paquetes VSPackage mediante código administrado. Proporcionan implementaciones predeterminadas para muchas interfaces de VSPackage. Al ocultar los detalles y las complejidades de la implementación, MPF permite crear productos de integración de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] con una cantidad mínima de código.  
  
> [!WARNING]
> La mayoría de los ensamblados que contienen clases de Managed Package Framework se incluyen con el SDK de Visual Studio. Puede descargar el código fuente de Managed Package Framework for Projects en [Managed Package Framework for Projects](https://archive.codeplex.com/?p=mpfproj11).  
  
## <a name="mpf-namespaces"></a>Espacios de nombres de MPF  
 En la tabla siguiente se enumeran los espacios de nombres de MPF proporcionados por [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Espacio de nombres|Contenido|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contiene clases útiles para controlar errores de COM, constantes de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y ventanas de Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Incluye contenedores de código administrado para proyectos de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] , editores y MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Incluye clases de MPF base de las que se puede derivar una implementación de muchos objetos comunes de Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contiene las extensiones del diseñador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contiene las extensiones del diseñador de serialización de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contiene las extensiones del diseñador de CodeDOM de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] .|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Admite subtipos de proyectos (también conocidos como "tipos").|  
  
## <a name="see-also"></a>Consulte también  
 [VSPackages y Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [Uso de ensamblados de interoperabilidad de Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages y marco de trabajo de paquetes administrados](../misc/vspackages-and-the-managed-package-framework.md)