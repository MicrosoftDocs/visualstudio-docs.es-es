---
title: Soluciones de Visio
ms.date: 08/14/2019
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
ms.openlocfilehash: a79b3c9964a24daf0a12ab90f47fb5903d89cdd0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985511"
---
# <a name="visio-solutions"></a>Soluciones de Visio
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Visio. Puede usar los complementos de VSTO para automatizar Visio, ampliar las características de Visio o personalizar la interfaz de usuario de Visio.

 Para obtener más información sobre los complementos de VSTO, vea Introducción a [la programación de complementos](../vsto/getting-started-programming-vsto-add-ins.md) de VSTO y [arquitectura de complementos de](../vsto/architecture-of-vsto-add-ins.md)VSTO. Si no está familiarizado con la programación con Microsoft Office, consulte Introducción [&#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md).

 **Aplicación:** la información de este tema se aplica a los proyectos de complementos VSTO para Visio 2010. Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizar Visio mediante el modelo de objetos de Visio
 El modelo de objetos de Visio expone muchas clases que puede usar para automatizar Visio a fin de crear diagramas para organigramas, diagramas de flujo, escalas de tiempo del proyecto, diagramas de red, espacios de oficina, etc. La API permite escribir código para llevar a cabo tareas comunes:

- Construir y colocar formas y texto en los diagramas.

- Administrar el comportamiento de las formas de acuerdo con la lógica de negocios y los datos proporcionados por el usuario.

- Controlar la visualización de diagramas, como el modo de panorámica y el zoom.

- Personalizar la interfaz de usuario de la aplicación.

- Importar datos externos a Visio, vincularlos a formas y mostrarlos gráficamente en una página.

  Puede ver procedimientos paso a paso y ejemplos de código para usar el modelo de objetos de Visio para trabajar con documentos y formas en [trabajar con documentos de Visio](../vsto/working-with-visio-documents.md) y [trabajar con formas de Visio](../vsto/working-with-visio-shapes.md).

  Para obtener acceso al modelo de objetos de Visio desde un complemento de VSTO, use el campo `Application` de la clase `ThisAddIn` del proyecto. El campo `Application` devuelve un objeto `Microsoft.Office.Interop.Visio.Application` que representa la instancia actual de Visio. Para obtener más información, vea [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

  Cuando se llama al modelo de objetos de Visio, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario (PIA) para Visio. El PIA actúa como puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de Visio. Todo tipo de PIA de Visio se define en el espacio de nombres `Microsoft.Office.Interop.Visio`. Para obtener más información sobre los ensamblados de interoperabilidad primarios, vea [información general sobre el desarrollo de soluciones de office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md) y [ensamblados de interoperabilidad primario](../vsto/office-primary-interop-assemblies.md)

## <a name="visio-object-model-overview"></a>Información general sobre el modelo de objetos de Visio
 Puede encontrar información general sobre el modelo de objetos de Visio en [información general sobre el modelo de objetos](../vsto/visio-object-model-overview.md)de Visio, que incluye vínculos a la referencia del modelo de objetos de Visio y los SDK.

## <a name="customize-the-user-interface-of-visio"></a>Personalización de la interfaz de usuario de Visio
 La interfaz de usuario de Visio tiene las siguientes opciones de personalización.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Personalizar la cinta de opciones.|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|

 Para obtener información sobre cómo personalizar la interfaz de usuario de Visio, consulte la documentación de referencia de VBA correspondiente a la clase [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Consulte también
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md)
- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 en el desarrollo de Office](/previous-versions/office/developer/office-2010/ff604964(v=office.14))
