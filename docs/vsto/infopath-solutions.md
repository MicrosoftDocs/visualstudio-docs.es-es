---
title: Soluciones de InfoPath | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], InfoPath
- templates [Office development in Visual Studio], InfoPath
- InfoPath [Office development in Visual Studio]
- Office development in Visual Studio, InfoPath solutions
- projects [Office development in Visual Studio], InfoPath
- Office solutions [Office development in Visual Studio], InfoPath
- Office projects [Office development in Visual Studio], InfoPath
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 9db28542e4141767be55241b98e0a6b762b0e236
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="infopath-solutions"></a>Soluciones de InfoPath
  Visual Studio proporciona plantillas de proyecto que puede utilizar para crear complementos de VSTO para Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath no está disponible en Office 2016.  
  
> [!NOTE]  
>  Todavía puede crear un complemento de VSTO para InfoPath aunque haya instalado Office 2016. Solo tiene que instalar InfoPath 2013 u Office 2013 en paralelo con Office 2016.  
  
 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
 Los complementos de VSTO para InfoPath son similares a los complementos VSTO para otras aplicaciones de Microsoft Office. Estos tipos de soluciones constan de un ensamblado cargado por la aplicación. Los usuarios finales pueden tener acceso a la funcionalidad de este ensamblado independientemente del formulario o la plantilla de formulario que haya abiertos. Para obtener más información sobre los complementos de VSTO, consulte [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md) y [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
> [!NOTE]  
>  Visual Studio 2015 no incluye los proyectos de plantilla de formulario de InfoPath incorporados en versiones anteriores de Visual Studio. Tampoco puede utilizar Visual Studio 2015 para abrir o modificar un proyecto de plantilla de formulario de InfoPath creado en una versión anterior de Visual Studio. Sin embargo, puede abrir y editar un proyecto de plantilla de formulario de InfoPath con Visual Studio Tools para Aplicaciones. Para obtener más información, vea [Trabajar con proyectos de VSTO 2008 en InfoPath 2010](http://go.microsoft.com/fwlink/?LinkID=218903).  
  
## <a name="automating-infopath-by-using-an-add-in"></a>Automatizar InfoPath mediante un complemento  
 Para obtener acceso al modelo de objetos de InfoPath desde un complemento de VSTO para Office creado con las herramientas de desarrollo de Office en Visual Studio, utilice el campo `Application` de la clase `ThisAddIn` en el proyecto. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.InfoPath.Application> que representa la instancia actual de InfoPath. Para obtener más información, consulta [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
 Cuando llame al modelo de objetos de InfoPath desde un complemento de VSTO, utilice los tipos proporcionados en el ensamblado de interoperabilidad primario de InfoPath. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de InfoPath. Todos los tipos del ensamblado de interoperabilidad primario de InfoPath se definen en el espacio de nombres <xref:Microsoft.Office.Interop.InfoPath> . Para obtener más información sobre el ensamblado de interoperabilidad primario de InfoPath, vea [Acerca del ensamblado de interoperabilidad primario de Microsoft Office InfoPath](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72). Para obtener más información sobre los ensamblados de interoperabilidad primarios en general, vea [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="customizing-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizar la interfaz de usuario de InfoPath mediante un complemento  
 Al crear un complemento de VSTO para InfoPath, tiene varias opciones de personalización de la IU diferentes. En la tabla siguiente se enumeran algunas de estas opciones.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
|Agregar pestañas personalizadas a la cinta de opciones en InfoPath.|[Personalización de una cinta para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|  
  
 Para obtener más información acerca de cómo personalizar la interfaz de usuario de InfoPath y otras aplicaciones de Microsoft Office, consulte [personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md).  
  
## <a name="see-also"></a>Vea también  
 [Acerca del ensamblado de interoperabilidad primario de Microsoft Office InfoPath](http://msdn.microsoft.com/en-us/1b3ae03c-6951-49e4-a489-4712d3f7ba72)   
 [Getting Started Programming VSTO Add-ins](../vsto/getting-started-programming-vsto-add-ins.md)   
 [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)   
 [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)   
 [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)   
 [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md)   
 [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)   
 [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)   
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [InfoPath 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199012)  
  
  