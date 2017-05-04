---
title: "Migrar soluciones de Office a .NET Framework 4 o posterior | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.Project.TargetFrameworkWarning"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "proyectos de Office [desarrollo de Office en Visual Studio], migrar a .NET Framework 4"
ms.assetid: 31f6c48b-c086-4362-8629-f644d6083a44
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Migrar soluciones de Office a .NET Framework 4 o posterior
  Si el marco de trabajo de destino de un proyecto de Office se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior desde una versión anterior de .NET Framework, puede que sea necesario realizar algunos pasos adicionales para seguir ejecutando la solución en equipos de desarrollo y de usuario final. Para obtener más información, consulta [Cambios necesarios para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Además, puede que ya no se pueda compilar el proyecto. Algunas características de los proyectos de Office tienen diferentes modelos de programación para las distintas versiones de .NET Framework. Cuando se cambia el marco de trabajo de destino de un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior desde una versión anterior de .NET Framework, se deben realizar los siguientes cambios de código en el proyecto:  
  
-   [Actualizar proyectos de Excel y Word para migrarlos a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las personalizaciones de la Cinta en los proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-ribbon-customizations-in-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
-   [Actualizar las áreas del formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
 El marco de destino de un proyecto de Office cambia al actualizar ese proyecto desde una versión anterior de Visual Studio. Para obtener más información, consulta [Actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
 Para obtener más información acerca de por qué algunas características de los proyectos de Office tienen un modelo de programación diferente cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior, consulte [Cambios en el diseño de proyectos de Office destinados a .NET Framework 4 o .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) y [Información general sobre el Motor en tiempo de ejecución de Microsoft Visual Studio Tools para Office](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## Vea también  
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Cómo: Usar como destino una versión de .NET Framework](~/ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Solucionar problemas de errores de las soluciones de Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Soporte técnico adicional para errores de soluciones de Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  