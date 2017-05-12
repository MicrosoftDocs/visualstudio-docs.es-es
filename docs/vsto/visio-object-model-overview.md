---
title: "Informaci&#243;n general sobre el modelo de objetos de Visio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Visio [desarrollo de Office en Visual Studio], modelo de objeto"
  - "modelos de objeto [desarrollo de Office en Visual Studio], Office"
  - "modelos de objeto [desarrollo de Office en Visual Studio], Visio"
  - "objetos [desarrollo de Office en Visual Studio], modelos de objeto de Office"
  - "modelos de objetos de Office"
  - "modelo de objetos de Visio"
ms.assetid: 11f0ae0c-feff-46c7-9885-b968391718f7
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Informaci&#243;n general sobre el modelo de objetos de Visio
  Para desarrollar soluciones de Office para Microsoft Office Visio, puede interactuar con el modelo de objetos de Visio. Este modelo de objetos está compuesto por clases e interfaces que se proporcionan en el ensamblado de interoperabilidad primario de Visio y que se definen en el espacio de nombres Microsoft.Office.Interop.Visio.  
  
 En este tema se proporciona una breve introducción del modelo de objetos de Visio. Para obtener información sobre cómo usar el modelo de objetos de Visio para efectuar tareas en proyectos de Office, vea los siguientes temas:  
  
-   [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md)  
  
-   [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)  
  
## Comprender el modelo de objetos de Visio  
 Visio proporciona muchos objetos con los que puede interactuar. Estos objetos se organizan en una jerarquía que sigue estrechamente la interfaz de usuario. En la parte superior de la jerarquía se encuentra el objeto [Microsoft.Office.Interop.Visio.Application](HV10077088). Este objeto representa la instancia actual de Visio. El objeto Microsoft.Office.Interop.Visio.Application contiene los objetos Microsoft.Office.Interop.Visio.Document y Microsoft.Office.Interop.Visio.Page , así como las colecciones Microsoft.Office.Interop.Visio.Documents y Microsoft.Office.Interop.Visio.Pages. Cada uno de estos objetos y colecciones tiene muchos métodos y propiedades a los que puede acceder para manipular e interactuar con ella.  
  
 Para obtener más información, consulte la documentación de referencia de VBA para los objetos [Microsoft.Office.Interop.Visio.Application](HV10077088), [Microsoft.Office.Interop.Visio.Document](HV10077095) y [Microsoft.Office.Interop.Visio.Page](HV10077063) y también las colecciones [Microsoft.Office.Interop.Visio.Documents](HV10077062) y [Microsoft.Office.Interop.Visio.Pages](HV10077074).  
  
 En las siguientes secciones se describen brevemente los objetos de nivel superior y cómo interactúan entre sí. Estos objetos incluyen los siguientes objetos:  
  
-   Objeto de aplicación  
  
-   Document \(objeto\)  
  
-   Page \(objeto\)  
  
### Objeto de aplicación  
 El objeto Microsoft.Office.Interop.Visio.Application representa la aplicación de Visio y es el principal de los demás objetos. Sus miembros normalmente son aplicables a Visio en su totalidad. Puede usar las propiedades y métodos de los objetos Microsoft.Office.Interop.Visio.Application y Microsoft.Office.Interop.Visio.ApplicationSettings para controlar el entorno de Visio.  
  
 En los proyectos de complemento de VSTO, puede acceder al objeto Microsoft.Office.Interop.Visio.Application mediante el campo `Application` de la clase `ThisAddIn`. Para obtener más información, consulta [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
### Document \(objeto\)  
 El objeto Microsoft.Office.Interop.Visio.Document es fundamental para la programación de Visio. Representa un dibujo, una galería de símbolos o un archivo de plantilla. Al abrir un documento de Visio o crear uno nuevo, se crea un nuevo objeto Microsoft.Office.Interop.Visio.Document que se agrega a la colección Microsoft.Office.Interop.Visio.Documents del objeto Microsoft.Office.Interop.Visio.Application.  
  
 El documento que tiene el foco se denomina documento activo. Se representa mediante la propiedad Microsoft.Office.Interop.Visio.Application.ActiveDocument del objeto Microsoft.Office.Interop.Visio.Application.  
  
### Page \(objeto\)  
 El objeto Microsoft.Office.Interop.Visio.Page representa el área de dibujo de una página de primer plano o una página de segundo plano. Puede usar la propiedad Microsoft.Office.Interop.Visio.Page.Background para determinar si una página es una página de primer o segundo plano.  
  
 Para crear formas, puede usar métodos que incluyan los métodos Microsoft.Office.Interop.Visio.Page.DrawSpline y Microsoft.Office.Interop.Visio.Page.DrawOval. Además, puede recuperar los patrones de las galerías de símbolos y colocar las formas en una página mediante los métodos Microsoft.Office.Interop.Visio.Page.Drop o Microsoft.Office.Interop.Visio.Page.DropMany.  
  
## Usar la documentación del modelo de objetos de Visio  
 Para obtener una información completa sobre el modelo de objetos de Visio, consulte la referencia del modelo de objetos de Visio VBA. La referencia del modelo de objetos de VBA documenta el modelo de objetos de Excel tal como se expone al código de Visual Basic para Aplicaciones \(VBA\). Para obtener más información, vea la [Referencia 2010 del modelo de objetos de Visio](http://go.microsoft.com/fwlink/?LinkId=199775).  
  
 Todos los objetos y miembros de la referencia del modelo de objetos de VBA corresponden a tipos y miembros del ensamblado de interoperabilidad primario \(PIA\) de Visio. Por ejemplo, el objeto Document en la referencia del modelo de objetos VBA corresponde al tipo Microsoft.Office.Interop.Visio.Document del PIA de Visio. Aunque la referencia del modelo de objetos VBA proporciona ejemplos de código para la mayoría de las propiedades, métodos y eventos, debe traducir el código VBA de esta referencia a Visual Basic o Visual C\# si quiere usarlo en un proyecto de complemento de VSTO de Visio creado con Visual Studio.  
  
> [!NOTE]  
>  En este momento, no hay ninguna documentación de referencia para el ensamblado de interoperabilidad primario de Visio.  
  
 Si desea ver ejemplos de código relacionados y herramientas adicionales para crear soluciones de Visio, consulte [Visio 2010 Software Development Kit](http://go.microsoft.com/fwlink/?LinkId=196501).  
  
### Tipos adicionales en ensamblados de interoperabilidad primarios  
 Puede buscar tipos en los ensamblados de interoperabilidad primarios que no se puedan ver en VBA debido a diferencias de implementación. VBA proporciona una vista del modelo de objetos de Visio que solo incluye los objetos y miembros que se pueden usar directamente. Los ensamblados de interoperabilidad primarios exponen el mismo modelo de objetos, pero también incluyen otras interfaces, clases y miembros que traducen objetos del modelo de objetos COM a código administrado. Estos elementos adicionales no están diseñados para usarse directamente en el código.  
  
 Para obtener más información, consulte [Información general de clases e interfaces de los Ensamblados de interoperabilidad primarios de Office](http://go.microsoft.com/fwlink/?LinkId=189592) y [Ensamblados de interoperabilidad primarios de Office](../vsto/office-primary-interop-assemblies.md).  
  
## Vea también  
 [Soluciones de Visio](../vsto/visio-solutions.md)   
 [Trabajar con documentos de Visio](../vsto/working-with-visio-documents.md)   
 [Trabajar con formas de Visio](../vsto/working-with-visio-shapes.md)  
  
  