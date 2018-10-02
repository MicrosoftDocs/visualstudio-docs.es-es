---
title: Clases de Managed Package Framework | Documentos de Microsoft
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-csharp
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- managed package framework, helper classes
- managed package helper classes
- Visual Studio SDK, managed package helper classes
- classes [Visual Studio SDK], managed package framework
ms.assetid: 15aedcc3-c79a-460b-b620-43223f1ae81e
caps.latest.revision: 24
manager: douge
ms.openlocfilehash: 38f159df52c99554ed931269f29ad57e72745b5d
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47580816"
---
# <a name="managed-package-framework-classes"></a>Clases de Managed Package Framework
Las clases de Managed Package Framework (MPF) se pueden usar para crear paquetes VSPackage mediante código administrado. Proporcionan implementaciones predeterminadas para muchas interfaces de VSPackage. Al ocultar las complejidades y los detalles de implementación, MPF permite crear [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] productos de integración con una cantidad mínima de código.  
  
> [!WARNING]
>  La mayoría de los ensamblados que contienen clases de Managed Package Framework se incluyen con el SDK de Visual Studio. Puede descargar el código fuente de Managed Package Framework for Projects en [Managed Package Framework for Projects](http://mpfproj11.codeplex.com/).  
  
## <a name="mpf-namespaces"></a>Espacios de nombres de MPF  
 La tabla siguiente enumeran los espacios de nombres MPF proporcionados por el [!INCLUDE[vsipsdk](../includes/vsipsdk-md.md)].  
  
|Espacio de nombres|Contenido|  
|----------------|--------------|  
|<xref:Microsoft.VisualStudio>|Contiene clases útiles para controlar los errores de COM, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] constantes y las ventanas de Win32.|  
|<xref:Microsoft.VisualStudio.Package>|Incluye contenedores de código administrado para [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] proyectos, editores y MSBuild.|  
|<xref:Microsoft.VisualStudio.Shell>|Incluye clases de MPF base de las que se puede derivar una implementación de muchos objetos comunes de Visual Studio.|  
|<xref:Microsoft.VisualStudio.Shell.Design>|Contiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] las extensiones del diseñador.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization>|Contiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensiones del Diseñador de serialización.|  
|<xref:Microsoft.VisualStudio.Shell.Design.Serialization.CodeDom>|Contiene [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] extensiones del Diseñador de CodeDom.|  
|<xref:Microsoft.VisualStudio.Shell.Flavor>|Admite subtipos de proyectos (también conocidos como "tipos").|  
  
## <a name="see-also"></a>Vea también  
 [VSPackages y Managed Package Framework](../misc/vspackages-and-the-managed-package-framework.md)   
 [Mediante ensamblados de interoperabilidad de Visual Studio](../extensibility/internals/using-visual-studio-interop-assemblies.md)   
 [VSPackages y marco de trabajo de paquetes administrados](../misc/vspackages-and-the-managed-package-framework.md)