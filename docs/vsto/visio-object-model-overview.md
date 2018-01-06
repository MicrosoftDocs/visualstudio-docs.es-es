---
title: "Información general del modelo de objetos de Visio | Documentos de Microsoft"
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
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
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: "21"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 0ba481206e24870e0772290beba129d373c30862
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="visio-object-model-overview"></a>Información general sobre el modelo de objetos de Visio
  Para desarrollar soluciones de Office para Microsoft Office Visio, puede interactuar con el modelo de objetos de Visio. Este modelo de objetos está compuesto de clases e interfaces que se proporcionan en el ensamblado de interoperabilidad primario de Visio y se definen en el espacio de nombres Microsoft.Office.Interop.Visio.  
  
 En este tema se proporciona una breve introducción del modelo de objetos de Visio. Para obtener información sobre cómo usar el modelo de objetos de Visio para efectuar tareas en proyectos de Office, vea los siguientes temas:  
  
-   [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md)  
  
-   [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)  
  
## <a name="understanding-the-visio-object-model"></a>Comprender el modelo de objetos de Visio  
 Visio proporciona muchos objetos con los que puede interactuar. Estos objetos se organizan en una jerarquía que sigue estrechamente la interfaz de usuario. En la parte superior de la jerarquía se encuentra el objeto [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx) . Este objeto representa la instancia actual de Visio. El objeto Microsoft.Office.Interop.Visio.Application contiene los objetos Microsoft.Office.Interop.Visio.Document y Microsoft.Office.Interop.Visio.Page, así como el Microsoft.Office.Interop.Visio.Documents y Microsoft.Office.Interop.Visio.Pages colecciones. Cada uno de estos objetos y colecciones tiene muchos métodos y propiedades a los que puede acceder para manipular e interactuar con ella.  
  
 Para obtener más información, consulte la documentación de referencia de VBA para los objetos [Microsoft.Office.Interop.Visio.Application](https://msdn.microsoft.com/library/office/ff766485.aspx), [Microsoft.Office.Interop.Visio.Document](https://msdn.microsoft.com/library/office/ff765575.aspx)y [Microsoft.Office.Interop.Visio.Page](https://msdn.microsoft.com/library/office/ff767035.aspx) y también las colecciones [Microsoft.Office.Interop.Visio.Documents](https://msdn.microsoft.com/library/office/ff768812.aspx) y [Microsoft.Office.Interop.Visio.Pages](https://msdn.microsoft.com/library/office/ff766165.aspx) .  
  
 En las siguientes secciones se describen brevemente los objetos de nivel superior y cómo interactúan entre sí. Estos objetos incluyen los siguientes objetos:  
  
-   Objeto de aplicación  
  
-   Document (objeto)  
  
-   Page (objeto)  
  
### <a name="application-object"></a>Objeto de aplicación  
 El objeto Microsoft.Office.Interop.Visio.Application representa la aplicación de Visio y es el elemento primario de todos los demás objetos. Sus miembros normalmente son aplicables a Visio en su totalidad. Puede usar las propiedades y métodos de la Microsoft.Office.Interop.Visio.Application y los objetos Microsoft.Office.Interop.Visio.Application para controlar el entorno de Visio.  
  
 En los proyectos de complemento de VSTO, se puede obtener acceso al objeto Microsoft.Office.Interop.Visio.Application mediante el uso de la `Application` campo de la `ThisAddIn` clase. Para obtener más información, consulta [Programming VSTO Add-Ins](../vsto/programming-vsto-add-ins.md).  
  
### <a name="document-object"></a>Document (objeto)  
 El objeto Microsoft.Office.Interop.Visio.Document es fundamental para la programación de Visio. Representa un dibujo, una galería de símbolos o un archivo de plantilla. Al abrir un documento de Visio o crear un nuevo documento, cree un nuevo objeto Microsoft.Office.Interop.Visio.Document, que se agrega a la colección Microsoft.Office.Interop.Visio.Documents del objeto Microsoft.Office.Interop.Visio.Application .  
  
 El documento que tiene el foco se denomina documento activo. Se representa mediante la propiedad Microsoft.Office.Interop.Visio.Application.ActiveDocument del objeto Microsoft.Office.Interop.Visio.Application.  
  
### <a name="page-object"></a>Page (objeto)  
 El objeto Microsoft.Office.Interop.Visio.Page representa el área de dibujo de una página de primer plano o una página de fondo. Puede usar la propiedad Microsoft.Office.Interop.Visio.Page.Background para determinar si una página es una página de primer plano o en segundo plano.  
  
 Para crear formas, puede utilizar métodos que incluyan los métodos Microsoft.Office.Interop.Visio.Page.DrawSpline y Microsoft.Office.Interop.Visio.Page.DrawOval. Además, puede recuperar los patrones de las galerías de símbolos y colocar las formas en una página mediante los métodos Microsoft.Office.Interop.Visio.Page.Drop o Microsoft.Office.Interop.Visio.Page.DROP.  
  
## <a name="using-the-visio-object-model-documentation"></a>Usar la documentación del modelo de objetos de Visio  
 Para obtener una información completa sobre el modelo de objetos de Visio, consulte la referencia del modelo de objetos de Visio VBA. La referencia del modelo de objetos de VBA documenta el modelo de objetos de Excel tal como se expone al código de Visual Basic para Aplicaciones (VBA). Para obtener más información, vea la [Referencia 2010 del modelo de objetos de Visio](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del ensamblado de interoperabilidad primario (PIA) de Visio. Por ejemplo, el objeto de documento en la referencia del modelo de objetos VBA corresponde al tipo Microsoft.Office.Interop.Visio.Document en los PIA de Visio. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C# si quiere usarlo en un proyecto de complemento de VSTO de Visio creado con Visual Studio.  
  
> [!NOTE]  
>  En este momento, no hay ninguna documentación de referencia para el ensamblado de interoperabilidad primario de Visio.  
  
 Si desea ver ejemplos de código relacionados y herramientas adicionales para crear soluciones de Visio, consulte [Visio 2010 Software Development Kit](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### <a name="additional-types-in-primary-interop-assemblies"></a>Tipos adicionales en ensamblados de interoperabilidad primarios  
 Puede buscar tipos en los ensamblados de interoperabilidad primarios que no se puedan ver en VBA debido a diferencias de implementación. VBA proporciona una vista del modelo de objetos de Visio que solo incluye los objetos y miembros que se pueden usar directamente. Los ensamblados de interoperabilidad primarios exponen el mismo modelo de objetos, pero también incluyen otras interfaces, clases y miembros que traducen objetos del modelo de objetos COM a código administrado. Estos elementos adicionales no están diseñados para usarse directamente en el código.  
  
 Para obtener más información, consulta [Información general de clases e interfaces de los Ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=189592) y [Office Primary Interop Assemblies](../vsto/office-primary-interop-assemblies.md).  
  
## <a name="see-also"></a>Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md)   
 [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)  
  
  