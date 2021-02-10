---
title: Aplicaciones de Office de destino mediante ensamblados de interoperabilidad primarios
description: Obtenga información acerca de cómo puede usar Visual Studio para dirigirse a aplicaciones Microsoft Office mediante programación a través de ensamblados de interoperabilidad primarios.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- assemblies [Office development in Visual Studio], PIA references
- primary interop assemblies [Office development in Visual Studio], adding references to
- Office primary interop assemblies in Visual Studio, adding references to
- Office applications [Office development in Visual Studio], automating
- application development [Office development in Visual Studio], automating
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 11a0db0e23cf5512a6568ba5b66e0c18e563bd12
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962384"
---
# <a name="how-to-target-office-applications-through-primary-interop-assemblies"></a>Cómo: dirigirse a aplicaciones de Office a través de ensamblados de interoperabilidad primarios
  Cuando se crea un nuevo proyecto de Office, Visual Studio agrega automáticamente las referencias a los ensamblados de interoperabilidad primarios (PIA) de Microsoft Office necesarios para compilar el proyecto. Debe agregar referencias a otros PIA en los escenarios siguientes:

- Desea usar las características de otras aplicaciones de Microsoft Office en su proyecto. Por ejemplo, quizás le interese usar las características de Microsoft Office Excel en un proyecto de Microsoft Office Word.

- Desea automatizar las aplicaciones de Microsoft Office que no tienen proyectos dedicados en Visual Studio, como Microsoft Office Access.

  [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="to-add-a-reference-to-a-primary-interop-assembly"></a>Para agregar una referencia a un ensamblado de interoperabilidad primario

1. Abra el proyecto de Office y seleccione el nombre del proyecto en **Explorador de soluciones**.

2. En el menú **Proyecto**, haga clic en **Agregar referencia**.

3. En la pestaña **marco** , seleccione el Pia que desee en la lista **nombre de componente** . Para obtener más información sobre los ensamblados de interoperabilidad primarios disponibles Microsoft Office, vea [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).

     Si el proyecto tiene como destino [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o una versión posterior, la propiedad **incrustar tipos de interoperabilidad** de la referencia de ensamblado se establece en **true** de forma predeterminada. Con esta configuración, la solución no requiere el PIA en los equipos de los usuarios finales. Para obtener más información, vea [diseñar y crear soluciones de Office](../vsto/designing-and-creating-office-solutions.md).

    > [!NOTE]
    > En los proyectos de Office, agregue siempre referencias a los PIA de Office mediante la pestaña **.net** del cuadro de diálogo **Agregar referencia** en lugar de la pestaña **com** . Para obtener más información, vea [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).

4. Haga clic en **OK**.

     El nombre del ensamblado aparece en la carpeta **referencias** de **Explorador de soluciones**.

## <a name="see-also"></a>Vea también
- [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md)
