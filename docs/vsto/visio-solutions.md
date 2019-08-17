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
ms.openlocfilehash: 69d795fe9e4243bbce51e1e137bb6704492bae32
ms.sourcegitcommit: 209ed0fcbb8daa1685e8d6b9a97f3857a4ce1152
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/16/2019
ms.locfileid: "69551277"
---
# <a name="visio-solutions"></a>Soluciones de Visio
  Visual Studio proporciona plantillas de proyecto que puede usar para crear complementos de VSTO para Microsoft Office Visio. Puede usar los complementos de VSTO para automatizar Visio, ampliar las características de Visio o personalizar la interfaz de usuario de Visio.

 Para obtener más información sobre los complementos de VSTO, vea Introducción a [la programación](../vsto/getting-started-programming-vsto-add-ins.md) de complementos de VSTO y [arquitectura de complementos de](../vsto/architecture-of-vsto-add-ins.md)VSTO. Si no está familiarizado con la programación con Microsoft Office, consulte Introducción al [desarrollo de &#40;Office&#41;en Visual Studio](../vsto/getting-started-office-development-in-visual-studio.md).

 **Se aplica a:** La información de este tema se aplica a los proyectos de complemento de VSTO para Visio 2010. Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).

[!include[Add-ins note](includes/addinsnote.md)]

## <a name="automate-visio-by-using-the-visio-object-model"></a>Automatizar Visio mediante el modelo de objetos de Visio
 El modelo de objetos de Visio expone muchas clases que puede usar para automatizar Visio a fin de crear diagramas para organigramas, diagramas de flujo, escalas de tiempo del proyecto, diagramas de red, espacios de oficina, etc. La API permite escribir código para llevar a cabo tareas comunes:

- Construir y colocar formas y texto en los diagramas.

- Administrar el comportamiento de las formas de acuerdo con la lógica de negocios y los datos proporcionados por el usuario.

- Controlar la visualización de diagramas, como el modo de panorámica y el zoom.

- Personalizar la interfaz de usuario de la aplicación.

- Importar datos externos a Visio, vincularlos a formas y mostrarlos gráficamente en una página.

  Puede ver procedimientos paso a paso y ejemplos de código para usar el modelo de objetos de Visio para trabajar con documentos y formas en [trabajar con documentos de Visio](../vsto/working-with-visio-documents.md) y [trabajar con formas de Visio](../vsto/working-with-visio-shapes.md).

  Para obtener acceso al modelo de objetos de Visio desde un complemento de VSTO, use el campo `Application` de la clase `ThisAddIn` del proyecto. El campo `Application` devuelve un objeto `Microsoft.Office.Interop.Visio.Application` que representa la instancia actual de Visio. Para obtener más información, vea complementos de [VSTO de programas](../vsto/programming-vsto-add-ins.md).

  Cuando se llama al modelo de objetos de Visio, se usan los tipos que se proporcionan en el ensamblado de interoperabilidad primario (PIA) para Visio. El PIA actúa como puente entre el código administrado del complemento de VSTO y el modelo de objetos COM de Visio. Todo tipo de PIA de Visio se define en el espacio de nombres `Microsoft.Office.Interop.Visio`. Para obtener más información sobre los ensamblados de interoperabilidad primarios, vea [información &#40;&#41; general](../vsto/office-solutions-development-overview-vsto.md) sobre el desarrollo de soluciones de Office y ensamblados de interoperabilidad [primarios](../vsto/office-primary-interop-assemblies.md)

## <a name="visio-object-model-overview"></a>Información general sobre el modelo de objetos de Visio
 Puede encontrar información general sobre el modelo de objetos de Visio en [información general sobre el modelo de objetos](../vsto/visio-object-model-overview.md)de Visio, que incluye vínculos a la referencia del modelo de objetos de Visio y los SDK.

## <a name="customize-the-user-interface-of-visio"></a>Personalización de la interfaz de usuario de Visio
 La interfaz de usuario de Visio tiene las siguientes opciones de personalización.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Personalizar la cinta de opciones.|[Información general sobre la cinta](../vsto/ribbon-overview.md)|

 Para obtener información sobre cómo personalizar la interfaz de usuario de Visio, consulte la documentación de referencia de VBA correspondiente a la clase [Visio.UIObject](/office/vba/api/Visio.UIObject) .

## <a name="see-also"></a>Vea también
- [Introducción a la programación de complementos de VSTO](../vsto/getting-started-programming-vsto-add-ins.md)
- [Información general sobre &#40;el desarrollo de soluciones de Office VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md)
- [Arquitectura de complementos VSTO](../vsto/architecture-of-vsto-add-ins.md)
- [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md)
- [Complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md)
- [Escribir código en soluciones de Office](../vsto/writing-code-in-office-solutions.md)
- [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md)
- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Información general sobre el modelo de objetos de Visio](../vsto/visio-object-model-overview.md)
- [Visio 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199017)
