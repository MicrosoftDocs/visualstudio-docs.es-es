---
title: Soluciones de Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office projects [Office development in Visual Studio], Visio
- solutions [Office development in Visual Studio], Visio
- Visio [Office development in Visual Studio]
- templates [Office development in Visual Studio], Visio
- projects [Office development in Visual Studio], Visio
- Office solutions [Office development in Visual Studio], Visio
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: d2e47227f9da4e691575b7136011deff15db25db
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63438742"
---
# <a name="visio-solutions"></a>Soluciones de Visio
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Visio. Puede usar los complementos de VSTO para automatizar Visio, ampliar las características de Visio o personalizar la interfaz de usuario de Visio.

 Para obtener más información sobre los complementos VSTO, consulte [empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md) y [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md). Si está familiarizado con la programación con Microsoft Office, consulte [comenzar &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Se aplica a:** La información de este tema se aplica a proyectos de complemento VSTO para Visio 2010. Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

> [!NOTE]
> ¿Está interesado en desarrollar soluciones que amplían la experiencia de Office a través de [varias plataformas](https://dev.office.com/add-in-availability)? Visite el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizar Visio mediante el modelo de objetos de Visio
 El modelo de objetos de Visio expone muchas clases que puede usar para automatizar Visio a fin de crear diagramas para organigramas, diagramas de flujo, escalas de tiempo del proyecto, diagramas de red, espacios de oficina, etc. La API permite escribir código para llevar a cabo tareas comunes:

- Construir y colocar formas y texto en los diagramas.

- Administrar el comportamiento de las formas de acuerdo con la lógica de negocios y los datos proporcionados por el usuario.

- Controlar la visualización de diagramas, como el modo de panorámica y el zoom.

- Personalizar la interfaz de usuario de la aplicación.

- Importar datos externos a Visio, vincularlos a formas y mostrarlos gráficamente en una página.

  Puede ver los procedimientos paso a paso y ejemplos de código para usar el modelo de objetos de Visio para trabajar con documentos y formas en [trabajar con documentos de Visio](../vsto/working-with-visio-documents.md) y [trabajar con formas de Visio](../vsto/working-with-visio-shapes.md).

  Para obtener acceso al modelo de objetos de Visio desde un complemento de VSTO, use el campo `Application` de la clase `ThisAddIn` del proyecto. El campo `Application` devuelve un objeto `Microsoft.Office.Interop.Visio.Application` que representa la instancia actual de Visio. Para obtener más información, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).

  Cuando se llama al modelo de objetos de Visio, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario (PIA) para Visio. El PIA actúa como puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de Visio. Todo tipo de PIA de Visio se define en el espacio de nombres `Microsoft.Office.Interop.Visio`. Para obtener más información sobre los ensamblados de interoperabilidad primarios, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41; ](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).

## <a name="visio-object-model-overview"></a>Información general sobre el modelo de objetos de Visio
 Puede encontrar información general sobre el modelo de objetos de Visio en [información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md), que incluye vínculos a la referencia del modelo de objetos de Visio y el SDK.

## <a name="customize-the-user-interface-of-visio"></a>Personalizar la interfaz de usuario de Visio
 La interfaz de usuario de Visio tiene las siguientes opciones de personalización.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Personalizar la cinta de opciones.|[Información general sobre la cinta](../vsto/ribbon-overview.md)|

 Para obtener información sobre cómo personalizar la interfaz de usuario de Visio, consulte la documentación de referencia de VBA correspondiente a la clase [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Vea también
- [Empezar a programar complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Programar complementos VSTO](../vsto/programming-vsto-add-ins.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199017)
