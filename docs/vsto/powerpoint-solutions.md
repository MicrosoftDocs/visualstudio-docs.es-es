---
title: Soluciones de PowerPoint
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office solutions [Office development in Visual Studio], PowerPoint
- templates [Office development in Visual Studio], PowerPoint
- solutions [Office development in Visual Studio], PowerPoint
- projects [Office development in Visual Studio], PowerPoint
- PowerPoint [Office development in Visual Studio]
- Office projects [Office development in Visual Studio], PowerPoint
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7f2ecd0adea8e3d71eebff6e532a44def68c01c8
ms.sourcegitcommit: 2da366ba9ad124366f6502927ecc720985fc2f9e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2019
ms.locfileid: "68872049"
---
# <a name="powerpoint-solutions"></a>Soluciones de PowerPoint
  Visual Studio ofrece plantillas de proyecto que puede usarse para crear complementos de VSTO para Microsoft Office Outlook. Los complementos de VSTO se pueden usar para automatizar PowerPoint, ampliar las características de PowerPoint o personalizar la interfaz de usuario (UI) de PowerPoint.

 Para obtener más información sobre los complementos de VSTO, vea Introducción a [la programación](../vsto/getting-started-programming-vsto-add-ins.md) de complementos de VSTO y [arquitectura de complementos de](../vsto/architecture-of-vsto-add-ins.md)VSTO. Si no está familiarizado con la programación con Microsoft Office, consulte Introducción al [desarrollo de &#40;Office&#41;en Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]

> [!NOTE]
> ¿Está interesado en desarrollar soluciones que amplíen la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Consulte el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Los complementos de Office tienen una pequeña superficie en comparación con las soluciones y los complementos de VSTO, y puede compilarlos con casi cualquier tecnología de programación web, como HTML5, JavaScript, CSS3 y XML.

 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") Para ver una demostración en vídeo relacionada, vea [cómo: ¿Crear un complemento para Microsoft PowerPoint? ](http://go.microsoft.com/fwlink/?LinkId=132767).

## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizar PowerPoint con el modelo de objetos de PowerPoint
 El modelo de objetos de PowerPoint expone muchos tipos que puede usar para automatizar PowerPoint. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:

- Crear y dar formato a presentaciones mediante programación.

- Agregar o quitar diapositivas de las presentaciones.

- Agregar formas a una diapositiva o cambiar las formas de una diapositiva.

  Para tener acceso al modelo de objetos de PowerPoint desde un complemento de VSTO, `Application` use el campo `ThisAddIn` de la clase en el proyecto. El `Application` campo devuelve un objeto de [aplicación](/previous-versions/office/developer/office-2010/ff764034(v=office.14)) que representa la instancia actual de PowerPoint. Para obtener más información, vea complementos de [VSTO de programas](../vsto/programming-vsto-add-ins.md).

  Cuando se llama al modelo de objetos de PowerPoint, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de PowerPoint. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de PowerPoint. Todos los tipos del ensamblado de interoperabilidad primario de PowerPoint se definen en el espacio de nombres [Microsoft. Office. Interop. PowerPoint](/previous-versions/office/developer/office-2010/ff763170(v=office.14)) . Para obtener más información sobre los ensamblados de interoperabilidad primarios, vea [información &#40;&#41; general](../vsto/office-solutions-development-overview-vsto.md) sobre el desarrollo de soluciones de Office y ensamblados de interoperabilidad [primarios](../vsto/office-primary-interop-assemblies.md)

## <a name="WordOMDocumentation"></a>Usar la documentación del modelo de objetos de PowerPoint
 Para obtener información completa sobre el modelo de objetos de PowerPoint, puede consultar la referencia del ensamblado de interoperabilidad primario (PIA) de PowerPoint y la referencia del modelo de objetos VBA.

### <a name="primary-interop-assembly-reference"></a>Referencia de ensamblado de interoperabilidad primario
 La documentación de referencia de los PIA de PowerPoint describe los tipos Del ensamblado de interoperabilidad primario para PowerPoint. Esta documentación está disponible en la siguiente ubicación: Referencia de ensamblado de interoperabilidad [primario de PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).

 Para obtener más información sobre el diseño del PIA de PowerPoint, como las diferencias entre las clases y las interfaces en el PIA y cómo se implementan los eventos en el PIA, consulte [información general de las clases e interfaces de los ensamblados](http://go.microsoft.com/fwlink/?LinkId=199885)de interoperabilidad primarios de Office.

### <a name="vba-object-model-reference"></a>Referencia del modelo de objetos de VBA
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de PowerPoint tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, vea [Referencia del modelo de objetos de PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)

 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del ensamblado de interoperabilidad primario (PIA) de PowerPoint. Por ejemplo, el objeto Presentation de la referencia del modelo de objetos VBA corresponde al tipo de [presentación](/previous-versions/office/developer/office-2010/ff761925(v=office.14)) del Pia de PowerPoint. Aunque la referencia del modelo de objetos de VBA proporciona ejemplos de código para la mayoría de las propiedades, los métodos y los eventos, debe traducir el código de VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de complemento de VSTO para PowerPoint creado con Visual Studio.

## <a name="customize-the-user-interface-of-powerpoint"></a>Personalización de la interfaz de usuario de PowerPoint
 Puede modificar la interfaz de usuario (UI) de PowerPoint de las siguientes maneras:

|Tarea|Para obtener más información|
|----------|--------------------------|
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|
|Agregar pestañas personalizadas a la cinta.|[Información general sobre la cinta](../vsto/ribbon-overview.md)|
|Agregar grupos personalizados a una pestaña integrada en la cinta.|[Cómo: Personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|

 Para obtener más información sobre cómo personalizar la interfaz de usuario de PowerPoint y otras aplicaciones Microsoft Office, consulte Personalización de la [interfaz de usuario de Office](../vsto/office-ui-customization.md).

## <a name="see-also"></a>Vea también
- [Tutorial: Crear el primer complemento de VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Información general sobre &#40;el desarrollo de soluciones de Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Procedimientos: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [PowerPoint 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199015)
