---
title: Soluciones de Project
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: c3364c778b8dfc290ef06b7daa5ba063ac31f3db
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/01/2018
ms.locfileid: "34692605"
---
# <a name="project-solutions"></a>Soluciones de Project
  [!INCLUDE[vs_dev12](../vsto/includes/vs-dev12-md.md)] incluye plantillas de proyecto que se pueden usar para crear complementos VSTO para Microsoft Office Project. Puede usar los complementos para automatizar Project, ampliar sus características o personalizar la interfaz de usuario.  
  
 Para obtener más información sobre los complementos VSTO, consulte [empezar a programar complementos VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [arquitectura de complementos](../vsto/architecture-of-vsto-add-ins.md). Si sabe cómo programar con Microsoft Office, consulte [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).  
  
 [!INCLUDE[appliesto_projallapp](../vsto/includes/appliesto-projallapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
## <a name="automate-project-by-using-the-project-object-model"></a>Automatizar project mediante el modelo de objeto de proyecto  
 El modelo de objetos de Project expone muchos tipos que se pueden usar para automatizar Project. Estos tipos le permiten escribir código para realizar tareas comunes, como crear y modificar las tareas de un proyecto mediante programación.  
  
 Para obtener acceso al modelo de objetos de Project desde un complemento VSTO, use el campo `Application` de la clase `ThisAddIn` en su proyecto. El `Application` campo devuelve un `Microsoft.Office.Interop.MsProject.Application` objeto que representa la instancia actual de Project. Para obtener más información, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
 Cuando se llama al modelo de objetos de Project, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de Project. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento VSTO y el modelo de objetos COM en Project. Todos los tipos en el ensamblado de interoperabilidad primario de Project se definen en el `Microsoft.Office.Interop.MSProject` espacio de nombres. Para obtener más información sobre los ensamblados de interoperabilidad primarios, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="use-the-project-object-model-documentation"></a>Usar la documentación del modelo de objetos de proyecto  
 Para obtener información completa sobre el modelo de objetos de Project, puede consultar la referencia del modelo de objetos de VBA para Project. La referencia del modelo de objetos de VBA documenta el modelo de objetos de Project a medida que se expone al código de Visual Basic para aplicaciones (VBA). Para obtener más información, consulte [referencia del modelo de objetos de Project 2010](http://go.microsoft.com/fwlink/?LinkId=199771).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y a miembros del ensamblado de interoperabilidad primario (PIA) de Project. Por ejemplo, el objeto de calendario en la referencia del modelo de objetos VBA corresponde a la `Microsoft.Office.Interop.MSProject.Calendar` tipo en el PIA de Project. Aunque la referencia del modelo de objetos de VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe convertir el código de VBA de esta referencia a Visual Basic o a Visual C# si desea utilizarlo en un proyecto de complemento VSTO de Project que cree mediante Visual Studio.  
  
> [!NOTE]  
>  Por el momento, no existe ninguna documentación de referencia sobre el ensamblado de interoperabilidad primario de Project.  
  
### <a name="infrastructure-types-in-the-project-primary-interop-assembly"></a>Tipos de infraestructura en el ensamblado de interoperabilidad primario de project  
 A medida que escriba el código que utiliza el PIA de Project, podrá observar que aparecen muchos tipos que no se describen en la referencia de VBA. Estos tipos adicionales ayudan a convertir los objetos del modelo de objetos basados en COM de Project a código administrado; no están pensados para su uso directo en el código.  
  
 Para obtener más información, consulte [información general de las clases e interfaces de los ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=189592).  
  
## <a name="customize-the-user-interface-of-project"></a>Personalizar la interfaz de usuario del proyecto  
 Puede personalizar la interfaz de usuario de Project de las siguientes maneras.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Agregar pestañas personalizadas a la cinta de opciones en Project|[Información general de la cinta de opciones](../vsto/ribbon-overview.md)|  
  
 Para obtener más información acerca de cómo personalizar la interfaz de usuario de Project y otras aplicaciones de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vea también  
 [Tutorial: Crear el primer complemento de VSTO para project](../vsto/walkthrough-creating-your-first-vsto-add-in-for-project.md)   
 [Empezar a programar complementos VSTO](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Project 2010 y Project Server 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199016)  
  
  