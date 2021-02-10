---
title: Migrar soluciones de Office al .NET Framework 4 o posterior
description: Obtenga información sobre cómo migrar soluciones de Office al .NET Framework 4 o posterior para que el proyecto siga funcionando.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VST.Project.TargetFrameworkWarning
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], migrating to .NET Framework 4
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 8c11b2f107414ac5ffb048d7c5e49609ba0b17b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99946142"
---
# <a name="migrate-office-solutions-to-the-net-framework-4-or-later"></a>Migrar soluciones de Office al .NET Framework 4 o posterior
  Si el marco de trabajo de destino de un proyecto de Office se cambia a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o posterior desde una versión anterior del .NET Framework, es posible que se requieran algunos pasos adicionales para seguir ejecutando la solución en los equipos de desarrollo y de usuario final. Para obtener más información, vea [cambios necesarios para ejecutar proyectos de Office migrados al .NET Framework 4 o al .NET Framework 4,5](../vsto/required-changes-to-run-office-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md).

 Además, puede que ya no se pueda compilar el proyecto. Algunas características de los proyectos de Office tienen diferentes modelos de programación para las distintas versiones de .NET Framework. Cuando se cambia el marco de trabajo de destino de un proyecto de Office a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o a una versión posterior desde una versión anterior de .NET Framework, se deben realizar los siguientes cambios de código en el proyecto:

- [Actualizar proyectos de Excel y Word que migre al .NET Framework 4 o al .NET Framework 4,5](../vsto/updating-excel-and-word-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

- [Actualizar las personalizaciones de la cinta de opciones en los proyectos de Office migrados al .NET Framework 4 o al .NET Framework 4,5](update-ribbon-customizations-in-office-projects-to-migrate-to-dotnet-framework-4-or-4-5.md)

- [Actualice las áreas de formulario en los proyectos de Outlook que migre al .NET Framework 4 o al .NET Framework 4,5](../vsto/updating-form-regions-in-outlook-projects-that-you-migrate-to-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md)

  El marco de destino de un proyecto de Office cambia al actualizar ese proyecto desde una versión anterior de Visual Studio. Para obtener más información, vea [actualizar y migrar soluciones de Office](../vsto/upgrading-and-migrating-office-solutions.md).

  Para obtener más información sobre por qué algunas características de los proyectos de Office tienen un modelo de programación diferente cuando el destino es [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, consulte [cambios en el diseño de proyectos de Office destinados a los .NET Framework 4 o .NET Framework 4,5](../vsto/changes-to-the-design-of-office-projects-that-target-the-dotnet-framework-4-or-the-dotnet-framework-4-5.md) y [Visual Studio Tools para Office Runtime](../vsto/visual-studio-tools-for-office-runtime-overview.md).

## <a name="see-also"></a>Vea también
- [Diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md)
- [Procedimiento: Usar una versión de .NET Framework como destino](../ide/visual-studio-multi-targeting-overview.md)
- [Solucionar errores en soluciones de Office](../vsto/troubleshooting-errors-in-office-solutions.md)
- [Compatibilidad adicional para errores en las soluciones de Office](../vsto/additional-support-for-errors-in-office-solutions.md)
