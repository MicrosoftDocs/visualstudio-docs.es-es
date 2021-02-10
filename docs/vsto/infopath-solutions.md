---
title: soluciones de InfoPath
description: Obtenga información sobre cómo puede usar Visual Studio para crear complementos de VSTO para Microsoft InfoPath 2013 e InfoPath 2010.
ms.custom: SEO-VS-2020
ms.date: 08/14/2019
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b3feab4a4b66ed2d6cf96fbccc8aaf1fb7de3bb6
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99962371"
---
# <a name="infopath-solutions"></a>soluciones de InfoPath
  Visual Studio proporciona plantillas de proyecto que puede utilizar para crear complementos de VSTO para Microsoft Office InfoPath 2013 e InfoPath 2010. InfoPath no está disponible en Office 2016.

> [!NOTE]
> Puede crear un complemento de VSTO para InfoPath aunque haya instalado Office 2016. Solo tiene que instalar InfoPath 2013 u Office 2013 en paralelo con Office 2016.

 [!INCLUDE[appliesto_infoallapp](../vsto/includes/appliesto-infoallapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 Los complementos de VSTO para InfoPath son similares a los complementos VSTO para otras aplicaciones de Microsoft Office. Estos tipos de soluciones constan de un ensamblado cargado por la aplicación. Los usuarios finales pueden tener acceso a la funcionalidad de este ensamblado independientemente del formulario o la plantilla de formulario que haya abiertos. Para obtener más información sobre los complementos de VSTO, vea Introducción a [la programación de complementos](../vsto/getting-started-programming-vsto-add-ins.md) de VSTO y [arquitectura de complementos de](../vsto/architecture-of-vsto-add-ins.md)VSTO.

> [!NOTE]
> Visual Studio 2015 no incluye los proyectos de plantilla de formulario de InfoPath incorporados en versiones anteriores de Visual Studio. Tampoco puede utilizar Visual Studio 2015 para abrir o modificar un proyecto de plantilla de formulario de InfoPath creado en una versión anterior de Visual Studio. Sin embargo, puede abrir y editar un proyecto de plantilla de formulario de InfoPath con Visual Studio Tools para Aplicaciones. Para obtener más información, vea [trabajar con proyectos de VSTO 2008 en InfoPath 2010.](/archive/blogs/infopath/working-with-vsto-2008-projects-in-infopath-2010)

## <a name="automate-infopath-by-using-an-add-in"></a>Automatizar InfoPath mediante un complemento
 Para obtener acceso al modelo de objetos de InfoPath desde un complemento de VSTO para Office creado con las herramientas de desarrollo de Office en Visual Studio, utilice el campo `Application` de la clase `ThisAddIn` en el proyecto. El campo `Application` devuelve un objeto <xref:Microsoft.Office.Interop.InfoPath.Application> que representa la instancia actual de InfoPath. Para obtener más información, vea [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

 Cuando se llama al modelo de objetos de InfoPath desde un complemento de VSTO, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario de InfoPath. El ensamblado de interoperabilidad primario actúa como un puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de InfoPath. Todos los tipos del ensamblado de interoperabilidad primario de InfoPath se definen en el espacio de nombres <xref:Microsoft.Office.Interop.InfoPath> . Para obtener más información acerca del ensamblado de interoperabilidad primario de InfoPath, vea [acerca del ensamblado de interoperabilidad primario de Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly). Para obtener más información sobre los ensamblados de interoperabilidad primarios en general, vea [información general sobre el desarrollo de soluciones de office &#40;&#41;VSTO](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primarios](../vsto/office-primary-interop-assemblies.md)

## <a name="customize-the-user-interface-of-infopath-by-using-an-add-in"></a>Personalizar la interfaz de usuario de InfoPath mediante un complemento
 Al crear un complemento de VSTO para InfoPath, tiene varias opciones de personalización de la interfaz de usuario diferentes. En la tabla siguiente se enumeran algunas de estas opciones.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|
|Agregar pestañas personalizadas a la cinta de opciones en InfoPath.|[Personalizar una cinta para InfoPath](../vsto/customizing-a-ribbon-for-infopath.md)|

 Para obtener más información sobre cómo personalizar la interfaz de usuario de InfoPath y otras aplicaciones Microsoft Office, consulte [Personalización](../vsto/office-ui-customization.md)de la interfaz de usuario de Office.

## <a name="see-also"></a>Vea también
- [Acerca del ensamblado de interoperabilidad primario de Microsoft Office InfoPath](/office/client-developer/infopath/external-automation/about-the-microsoft-office-infopath-primary-interop-assembly)
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [InfoPath 2010 en el desarrollo de Office](/previous-versions/office/developer/office-2010/ff604966(v=office.14))