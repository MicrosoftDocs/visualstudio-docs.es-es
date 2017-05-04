---
title: "Obtener acceso a un &#225;rea de formulario en tiempo de ejecuci&#243;n | Microsoft Docs"
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
  - "Inspectores [desarrollo de Office en Visual Studio]"
  - "Exploradores [desarrollo de Office en Visual Studio]"
  - "áreas del formulario [desarrollo de Office en Visual Studio], acceso en tiempo de ejecución"
ms.assetid: 58eaa9e0-acba-4a13-a6dd-b7e37a38156e
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Obtener acceso a un &#225;rea de formulario en tiempo de ejecuci&#243;n
  
  
|Se aplica a|  
|-----------------|  
|La información de este tema solamente se aplica a los siguientes tipos de proyectos y versiones de Microsoft Office. Para obtener más información, consulta [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo de proyecto**<br /><br /> -   Proyectos de complemento de VSTO<br /><br /> **Versión de Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  
  
 Utilice la clase `Globals` para acceder a áreas del formulario desde cualquier lugar dentro del proyecto de Outlook. Para obtener más información sobre la clase `Globals`, vea [Acceso global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  
  
 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  
  
## Acceso a áreas del formulario que aparecen en una ventana del Inspector de Outlook concreta  
 Para acceder a todas las áreas del formulario que aparecen en un Inspector de Outlook concreto, llame a la propiedad `FormRegions` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que represente el Inspector.  
  
 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en el Inspector que tiene actualmente el foco. Después, este ejemplo accede a un área del formulario de la colección denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#2)]
 [!code-vb[Trin_Outlook_FR_Access#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#2)]  
  
## Acceso a áreas del formulario que aparecen en una ventana concreta del Explorador de Outlook  
 Para acceder a todas las áreas del formulario que aparecen en un Explorador de Outlook concreto, llame a la propiedad `FormRegions` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> que represente el explorador.  
  
 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en el explorador que tiene actualmente el foco. Después, este ejemplo accede a un área del formulario de la colección denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#3)]
 [!code-vb[Trin_Outlook_FR_Access#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#3)]  
  
## Acceso a todas las áreas del formulario  
 Para acceder a todas las áreas del formulario que aparecen en todos los exploradores e inspectores, llame a la propiedad `FormRegions` de la clase `Globals`.  
  
 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en todos los exploradores e inspectores. En este ejemplo accede entonces a un área del formulario denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.  
  
 [!code-csharp[Trin_Outlook_FR_Access#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/CS/ThisAddIn.cs#1)]
 [!code-vb[Trin_Outlook_FR_Access#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Outlook_FR_Access/VB/ThisAddIn.vb#1)]  
  
## Acceso a controles en un área del formulario  
 Para acceder a los controles en un área de formulario mediante la clase `Globals`, debe conseguir que los controles sean accesibles para el código de fuera del archivo de código del área del formulario.  
  
### Áreas del formulario diseñadas en el diseñador de áreas del formulario  
 En C\#, cambie el modificador de cada control al que quiera tener acceso. Para ello, seleccione cada uno de los controles en el diseñador de áreas del formulario y cambie la propiedad **Modificadores** a **Internos** o **Públicos** en la ventana **Propiedades**. Por ejemplo, si cambia la propiedad **Modificador** de `textBox1` a **Interno**, puede acceder a `textBox1` si escribe `Globals.FormRegions.FormRegion1.textBox1`.  
  
 En Visual Basic no es necesario cambiar el modificador.  
  
### Áreas del formulario importadas  
 Al importar un área del formulario que se diseñó en Outlook, el modificador de acceso de cada control en el área del formulario pasa a ser privado. Como no se puede usar el diseñador de áreas del formulario para modificar un área del formulario importada, no hay ninguna manera de cambiar el modificador de un control en la ventana **Propiedades**.  
  
 Para habilitar el acceso a un control desde fuera del archivo de código del área del formulario, cree una propiedad en el archivo de código del área del formulario que devuelva dicho control.  
  
 Para más información sobre cómo crear propiedades en C\#, consulte [Cómo: Declarar y usar propiedades de lectura y escritura &#40;Guía de programación de C&#35;&#41;](../Topic/How%20to:%20Declare%20and%20Use%20Read%20Write%20Properties%20(C%23%20Programming%20Guide).md).  
  
 Para más información sobre cómo crear propiedades en Visual Basic, consulte [NO EN LA COMPILACIÓN: Cómo: Agregar campos y propiedades a una clase](http://msdn.microsoft.com/es-es/ae53f61b-3abc-413e-8931-703c5f5e8fc2).  
  
## Vea también  
 [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)  
  
  