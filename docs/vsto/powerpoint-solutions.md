---
title: Soluciones de PowerPoint
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8f836662b9dfe4df8e45e24a7210664b8cecd49e
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35673994"
---
# <a name="powerpoint-solutions"></a>Soluciones de PowerPoint
  Visual Studio ofrece plantillas de proyecto que puede usarse para crear complementos de VSTO para Microsoft Office Outlook. Los complementos de VSTO se pueden usar para automatizar PowerPoint, ampliar las características de PowerPoint o personalizar la interfaz de usuario (UI) de PowerPoint.  
  
 Para obtener más información sobre los complementos VSTO, consulte [empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Si está familiarizado con la programación con Microsoft Office, consulte [comenzar &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_pptallapp](../vsto/includes/appliesto-pptallapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en desarrollar soluciones que amplían la experiencia de Office a través de [varias plataformas](https://dev.office.com/add-in-availability)? Visite el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo al vídeo") para una demostración en vídeo relacionada, vea [¿cómo lo hago?: crear un complemento para Microsoft PowerPoint?](http://go.microsoft.com/fwlink/?LinkId=132767).  
  
## <a name="automate-powerpoint-by-using-the-powerpoint-object-model"></a>Automatizar PowerPoint usando el modelo de objetos de PowerPoint  
 El modelo de objetos de PowerPoint expone muchos tipos que puede usar para automatizar PowerPoint. Estos tipos le permiten escribir código para llevar a cabo tareas comunes:  
  
-   Crear y dar formato a presentaciones mediante programación.  
  
-   Agregar o quitar diapositivas de las presentaciones.  
  
-   Agregar formas a una diapositiva o cambiar las formas de una diapositiva.  
  
 Para acceder el modelo de objetos de PowerPoint desde un complemento de VSTO, use el `Application` campo de la `ThisAddIn` clase del proyecto. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.PowerPoint.Application> que representa la instancia actual de PowerPoint. Para obtener más información, consulte [programa VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Cuando se llama al modelo de objetos de PowerPoint, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de PowerPoint. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de PowerPoint. Todos los tipos del ensamblado de interoperabilidad primario de PowerPoint se definen en el espacio de nombres <xref:Microsoft.Office.Interop.PowerPoint> . Para obtener más información sobre los ensamblados de interoperabilidad primarios, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
##  <a name="WordOMDocumentation"></a> Utilice la documentación del modelo de objetos de PowerPoint  
 Para obtener información completa sobre el modelo de objetos de PowerPoint, puede consultar la referencia del ensamblado de interoperabilidad primario (PIA) de PowerPoint y la referencia del modelo de objetos VBA.  
  
### <a name="primary-interop-assembly-reference"></a>Referencia de ensamblado de interoperabilidad primario  
 La documentación de referencia de los PIA de PowerPoint describe los tipos Del ensamblado de interoperabilidad primario para PowerPoint. Esta documentación está disponible en la siguiente ubicación: [referencia de ensamblado de interoperabilidad primario de PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
 Para obtener más información sobre el diseño de los PIA de PowerPoint, como las diferencias entre las clases e interfaces en los PIA y cómo se implementan los eventos en lo PIA, consulte [información general de las clases e interfaces de los ensamblados de interoperabilidad primarios de Office ](http://go.microsoft.com/fwlink/?LinkId=199885).  
  
### <a name="vba-object-model-reference"></a>Referencia del modelo de objetos VBA  
 La referencia del modelo de objetos de VBA documenta el modelo de objetos de PowerPoint tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, consulte [referencia del modelo de objetos de PowerPoint 2010](http://go.microsoft.com/fwlink/?LinkId=199770)  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del ensamblado de interoperabilidad primario (PIA) de PowerPoint. Por ejemplo, el objeto de presentación de la referencia de modelo de objetos VBA corresponde a la <xref:Microsoft.Office.Interop.PowerPoint.Presentation> tipo en los PIA de PowerPoint. Aunque la referencia del modelo de objetos de VBA proporciona ejemplos de código para la mayoría de las propiedades, los métodos y los eventos, debe traducir el código de VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de complemento de VSTO para PowerPoint creado con Visual Studio.  
  
## <a name="customize-the-user-interface-of-powerpoint"></a>Personalizar la interfaz de usuario de PowerPoint  
 Puede modificar la interfaz de usuario (UI) de PowerPoint de las siguientes maneras:  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Agregar pestañas personalizadas a la cinta.|[Información general de la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregar grupos personalizados a una pestaña integrada en la cinta.|[Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md)|  
  
 Para obtener más información sobre cómo personalizar la interfaz de usuario de PowerPoint y otras aplicaciones de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear el primer complemento VSTO para PowerPoint](../vsto/walkthrough-creating-your-first-vsto-add-in-for-powerpoint.md)   
 [Empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [PowerPoint 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199015)  
  
  