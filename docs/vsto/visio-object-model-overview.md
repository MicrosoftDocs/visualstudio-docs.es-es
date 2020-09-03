---
title: Información general sobre el modelo de objetos de Visio
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visio [Office development in Visual Studio], object model
- object models [Office development in Visual Studio], Office
- object models [Office development in Visual Studio], Visio
- objects [Office development in Visual Studio], Office object models
- Office object models
- Visio object model
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 88695511d22e38262dc969d66e469441c9c3ac47
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72985479"
---
# <a name="visio-object-model-overview"></a>Información general sobre el modelo de objetos de Visio
  Para desarrollar soluciones de Office para Microsoft Office Visio, puede interactuar con el modelo de objetos de Visio. Este modelo de objetos está compuesto por clases e interfaces que se proporcionan en el ensamblado de interoperabilidad primario de Visio y que se definen en el espacio de nombres `Microsoft.Office.Interop.Visio`.

 En este tema se proporciona una breve introducción del modelo de objetos de Visio. Para obtener información sobre cómo usar el modelo de objetos de Visio para efectuar tareas en proyectos de Office, vea los siguientes temas:

- [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md)

- [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)

## <a name="understand-the-visio-object-model"></a>Descripción del modelo de objetos de Visio
 Visio proporciona muchos objetos con los que puede interactuar. Estos objetos se organizan en una jerarquía que sigue estrechamente la interfaz de usuario. En la parte superior de la jerarquía se encuentra el objeto [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application) . Este objeto representa la instancia actual de Visio. El `Microsoft.Office.Interop.Visio.Application` objeto contiene los `Microsoft.Office.Interop.Visio.Document` `Microsoft.Office.Interop.Visio.Page` objetos y, así como las `Microsoft.Office.Interop.Visio.Documents` `Microsoft.Office.Interop.Visio.Pages` colecciones y. Cada uno de estos objetos y colecciones tiene muchos métodos y propiedades a los que puede acceder para manipular e interactuar con ella.

 Para obtener más información, consulte la documentación de referencia de VBA para los objetos [Microsoft.Office.Interop.Visio.Application](/office/vba/api/Visio.Application), [Microsoft.Office.Interop.Visio.Document](/office/vba/api/Visio.Document)y [Microsoft.Office.Interop.Visio.Page](/office/vba/api/Visio.Page) y también las colecciones [Microsoft.Office.Interop.Visio.Documents](/office/vba/api/Visio.Documents) y [Microsoft.Office.Interop.Visio.Pages](/office/vba/api/Visio.Pages) .

 En las siguientes secciones se describen brevemente los objetos de nivel superior y cómo interactúan entre sí. Estos objetos incluyen los siguientes objetos:

- Objeto de aplicación

- Document (objeto)

- Page (objeto)

### <a name="application-object"></a>Objeto de aplicación
 El objeto Microsoft. Office. Interop. Visio. Application representa la aplicación Visio y es el elemento primario de todos los demás objetos. Sus miembros normalmente son aplicables a Visio en su totalidad. Puede usar las propiedades y los métodos de los objetos Microsoft. Office. Interop. Visio. Application y `Microsoft.Office.Interop.Visio.ApplicationSettings` para controlar el entorno de Visio.

 En los proyectos de complemento de VSTO, puede acceder al objeto Microsoft. Office. Interop. Visio. Application mediante el `Application` campo de la `ThisAddIn` clase. Para obtener más información, consulta [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).

### <a name="document-object"></a>Document (objeto)
 El objeto Microsoft.Office.Interop.Visio.Document es fundamental para programar Visio. Representa un dibujo, una galería de símbolos o un archivo de plantilla. Al abrir un documento de Visio o crear un nuevo documento, se crea un nuevo Microsoft.Office.Interop.Visio.Docobjeto ument, que se agrega a la colección Microsoft.Office.Interop.Visio.Documents del objeto Microsoft. Office. Interop. Visio. Application.

 El documento que tiene el foco se llama documento activo. Se representa mediante la `Microsoft.Office.Interop.Visio.Application.ActiveDocument` propiedad del objeto Microsoft. Office. Interop. Visio. Application.

### <a name="page-object"></a>Page (objeto)
 El objeto Microsoft. Office. Interop. Visio. Page representa el área de dibujo de una página de primer plano o una página de fondo. Puede usar la propiedad `Microsoft.Office.Interop.Visio.Page.Background` para determinar si una página es una página de primer o segundo plano.

 Para crear formas, puede usar métodos que incluyan los métodos `Microsoft.Office.Interop.Visio.Page.DrawSpline` y `Microsoft.Office.Interop.Visio.Page.DrawOval`. Además, puede recuperar los patrones de las galerías de símbolos y colocar las formas en una página mediante los métodos `Microsoft.Office.Interop.Visio.Page.Drop` o `Microsoft.Office.Interop.Visio.Page.DropMany`.

## <a name="use-the-visio-object-model-documentation"></a>Usar la documentación del modelo de objetos de Visio
 Para obtener una información completa sobre el modelo de objetos de Visio, consulte la referencia del modelo de objetos de Visio VBA. La referencia del modelo de objetos de VBA documenta el modelo de objetos de Excel tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, vea [Referencia del modelo de objetos de Visio](/office/vba/api/overview/visio/object-model).

 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del ensamblado de interoperabilidad primario (PIA) de Visio. Por ejemplo, el `Document` objeto de la referencia del modelo de objetos VBA corresponde al tipo Microsoft.Office.Interop.Visio.Document en el Pia de Visio. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de complemento de VSTO de Visio creado con Visual Studio.

> [!NOTE]
> En este momento, no hay ninguna documentación de referencia para el ensamblado de interoperabilidad primario de Visio.

 Para ver ejemplos de código relacionados y herramientas adicionales para crear soluciones de Visio, consulte [Kit de desarrollo de software de visio 2010](https://www.microsoft.com/download/details.aspx?id=12365).

### <a name="additional-types-in-primary-interop-assemblies"></a>Tipos adicionales en ensamblados de interoperabilidad primarios
 Puede buscar tipos en los ensamblados de interoperabilidad primarios que no se puedan ver en VBA debido a diferencias de implementación. VBA proporciona una vista del modelo de objetos de Visio que solo incluye los objetos y miembros que se pueden usar directamente. Los ensamblados de interoperabilidad primarios exponen el mismo modelo de objetos, pero también incluyen otras interfaces, clases y miembros que traducen objetos del modelo de objetos COM a código administrado. Estos elementos adicionales no están diseñados para usarse directamente en el código.

 Para obtener más información, vea [información general de clases e interfaces de los ensamblados de interoperabilidad primarios de Office](/previous-versions/office/office-12/ms247299(v=office.12)) y [ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).

## <a name="see-also"></a>Consulte también
- [Soluciones de Visio](../vsto/visio-solutions.md)
- [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md)
- [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)
