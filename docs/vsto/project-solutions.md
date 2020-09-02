---
title: Soluciones de proyecto
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- projects [Office development in Visual Studio], Project
- Office solutions [Office development in Visual Studio], Project
- Project [Office development in Visual Studio]
- templates [Office development in Visual Studio], Project
- Office projects [Office development in Visual Studio], Project
- solutions [Office development in Visual Studio], Project
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 84dfe7cf86df2139b06a320d1c6441665a08a1b1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985637"
---
# <a name="project-solutions"></a>Soluciones de proyecto
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] incluye plantillas de proyecto que se pueden usar para crear complementos VSTO para Microsoft Office Project. Puede usar los complementos para automatizar Project, ampliar sus características o personalizar la interfaz de usuario.

 Para obtener más información sobre los complementos de VSTO, vea Introducción a [la programación de complementos](../vsto/getting-started-programming-vsto-add-ins.md) de VSTO y [arquitectura de complementos de](../vsto/architecture-of-vsto-add-ins.md)VSTO. Si no está familiarizado con la programación con Microsoft Office, consulte Introducción [&#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-project-by-using-the-project-object-model"></a>Automatizar Project mediante el modelo de objetos de Project
 El modelo de objetos de Project expone muchos tipos que se pueden usar para automatizar Project. Estos tipos le permiten escribir código para realizar tareas comunes, como crear y modificar las tareas de un proyecto mediante programación.

 Para tener acceso al modelo de objetos de Project desde un complemento de VSTO, use el `Application` campo de la `ThisAddIn` clase en el proyecto. El `Application` campo devuelve un `Microsoft.Office.Interop.MsProject.Application` objeto que representa la instancia actual del proyecto. Para obtener más información, vea [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

 Cuando se llama al modelo de objetos de Project, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de Project. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento VSTO y el modelo de objetos COM en Project. Todos los tipos del ensamblado de interoperabilidad primario de Project se definen en el espacio de nombres `Microsoft.Office.Interop.MSProject`. Para obtener más información sobre los ensamblados de interoperabilidad primarios, vea [información general sobre el desarrollo de soluciones de office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primario](../vsto/office-primary-interop-assemblies.md)

## <a name="use-the-project-object-model-documentation"></a>Usar la documentación del modelo de objetos de Project
 Para obtener información completa sobre el modelo de objetos de Project, puede consultar la referencia del modelo de objetos de VBA para Project. La referencia del modelo de objetos de VBA documenta el modelo de objetos de Project a medida que se expone al código de Visual Basic para aplicaciones (VBA). Para obtener más información, vea [Referencia del modelo de objetos de Project](/office/vba/api/project.object).

 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y a miembros del ensamblado de interoperabilidad primario (PIA) de Project. Por ejemplo, el objeto de calendario de la referencia del modelo de objetos VBA corresponde al `Microsoft.Office.Interop.MSProject.Calendar` tipo del Pia del proyecto. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, los métodos y los eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C# Si desea utilizarlos en un proyecto de complemento de VSTO del proyecto que cree con Visual Studio.

> [!NOTE]
> Por el momento, no existe ninguna documentación de referencia sobre el ensamblado de interoperabilidad primario de Project.

### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipos de infraestructura del ensamblado de interoperabilidad primario de Project
 A medida que escriba el código que utiliza el PIA de Project, podrá observar que aparecen muchos tipos que no se describen en la referencia de VBA. Estos tipos adicionales ayudan a convertir los objetos del modelo de objetos basados en COM de Project a código administrado; no están pensados para su uso directo en el código.

 Para obtener más información, vea [información general de las clases e interfaces de los ensamblados de interoperabilidad primarios de Office](/previous-versions/office/office-12/ms247299(v=office.12)).

## <a name="customize-the-user-interface-of-project"></a>Personalización de la interfaz de usuario de Project
 Puede personalizar la interfaz de usuario de Project de las siguientes maneras.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Agregar pestañas personalizadas a la cinta de opciones en Project|[Información general sobre la cinta](../vsto/ribbon-overview.md)|

 Para obtener más información sobre cómo personalizar la interfaz de usuario de Project y otras aplicaciones Microsoft Office, consulte [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

## <a name="see-also"></a>Vea también
- [Tutorial: crear el primer complemento de VSTO para Project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Proyecto 2010 y Project Server 2010 en el desarrollo de Office](/previous-versions/office/developer/office-2010/ee758031(v=office.14))
