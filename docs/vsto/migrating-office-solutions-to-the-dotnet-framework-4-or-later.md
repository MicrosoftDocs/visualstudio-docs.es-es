---
title: Migrar soluciones de Office a .NET Framework 4 o posterior
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: a7e281f65f58cc3fa10325574eb397d0aa20308e
ms.sourcegitcommit: 159ed9d4f56cdc1dff2fd19d9dffafe77e46cd4e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2018
ms.locfileid: "53740018"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrar soluciones de Office a .NET Framework 4 o posterior
  Si se cambia la plataforma de destino de un proyecto de Office a la [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior desde una versión anterior de .NET Framework, algunos pasos adicionales pueden ser necesarios para seguir ejecutando la solución en equipos de desarrollo y del usuario final. Para obtener más información, consulte [los cambios requeridos para ejecutar proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).  
  
 Además, puede que ya no se pueda compilar el proyecto. Algunas características de los proyectos de Office tienen diferentes modelos de programación para las distintas versiones de .NET Framework. Cuando se cambia el marco de trabajo de destino de un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior desde una versión anterior de .NET Framework, se deben realizar los siguientes cambios de código en el proyecto:  
  
- [Actualizar proyectos de Excel y Word migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
- [Actualizar las personalizaciones de cinta de opciones en proyectos de Office migrados a .NET Framework 4 o .NET Framework 4.5](/visualstudio/vsto/update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5)  
  
- [Actualizar las áreas de formulario en los proyectos de Outlook migrados a .NET Framework 4 o .NET Framework 4.5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)  
  
  El marco de destino de un proyecto de Office cambia al actualizar ese proyecto desde una versión anterior de Visual Studio. Para obtener más información, consulte [actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).  
  
  Para obtener más información acerca de por qué algunas características de los proyectos de Office tienen un modelo de programación diferente cuando el destino es el [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, consulte [cambios en el diseño de proyectos de Office destinados a .NET Framework 4 o .NET Framework 4.5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) y [Visual Studio Tools para Office runtime overview](../vsto/visual-studio-tools-for-office-runtime-overview.md).  
  
## <a name="see-also"></a>Vea también  
 [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)   
 [Cómo: Una versión de .NET Framework de destino](../ide/how-to-target-a-version-of-the-dotnet-framework.md)   
 [Solución de problemas de errores en las soluciones de Office](../vsto/troubleshooting-errors-in-office-solutions.md)   
 [Soporte técnico adicional para errores en soluciones de Office](../vsto/additional-support-for-errors-in-office-solutions.md)  
  
  