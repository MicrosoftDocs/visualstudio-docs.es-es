---
title: Obtener acceso a un área de formulario en tiempo de ejecución | Documentos de Microsoft
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at run time
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e1a7d2ad69adff4462379f223f4f6bab397511d4
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="accessing-a-form-region-at-run-time"></a>Obtener acceso a un área de formulario en tiempo de ejecución


|Se aplica a|  
|----------------|  
|La información de este tema solamente se aplica a los siguientes tipos de proyectos y versiones de Microsoft Office. Para obtener más información, consulte [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo de proyecto**<br /><br /> : Proyectos de complemento de VSTO<br /><br /> **Versión de Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|  

 Utilice la clase `Globals` para acceder a áreas del formulario desde cualquier lugar dentro del proyecto de Outlook. Para obtener más información sobre la `Globals` de clases, consulte [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).  

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]  

## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Acceso a áreas del formulario que aparecen en una ventana del Inspector de Outlook concreta  
 Para acceder a todas las áreas del formulario que aparecen en un Inspector de Outlook concreto, llame a la propiedad `FormRegions` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que represente el Inspector.  

 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en el Inspector que tiene actualmente el foco. Después, este ejemplo accede a un área del formulario de la colección denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]  

## <a name="accessing-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Acceso a áreas del formulario que aparecen en una ventana concreta del Explorador de Outlook  
 Para acceder a todas las áreas del formulario que aparecen en un Explorador de Outlook concreto, llame a la propiedad `FormRegions` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> que represente el explorador.  

 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en el explorador que tiene actualmente el foco. Después, este ejemplo accede a un área del formulario de la colección denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]  

## <a name="accessing-all-form-regions"></a>Acceso a todas las áreas del formulario  
 Para acceder a todas las áreas del formulario que aparecen en todos los exploradores e inspectores, llame a la propiedad `FormRegions` de la clase `Globals` .  

 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en todos los exploradores e inspectores. En este ejemplo accede entonces a un área del formulario denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.  

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]  

## <a name="accessing-controls-on-a-form-region"></a>Acceso a controles en un área del formulario  
 Para acceder a los controles en un área de formulario mediante la clase `Globals` , debe conseguir que los controles sean accesibles para el código de fuera del archivo de código del área del formulario.  

### <a name="form-regions-designed-in-the-form-region-designer"></a>Áreas del formulario diseñadas en el diseñador de áreas del formulario  
 En C#, cambie el modificador de cada control al que quiera tener acceso. Para ello, seleccione cada uno de los controles en el diseñador de áreas del formulario y cambie la propiedad **Modificadores** a **Internos** o **Públicos** en la ventana **Propiedades** . Por ejemplo, si cambia la propiedad **Modificador** de `textBox1` a **Interno**, puede acceder a `textBox1` si escribe `Globals.FormRegions.FormRegion1.textBox1`.  

 En Visual Basic no es necesario cambiar el modificador.  

### <a name="imported-form-regions"></a>Áreas del formulario importadas  
 Al importar un área del formulario que se diseñó en Outlook, el modificador de acceso de cada control en el área del formulario pasa a ser privado. Como no se puede usar el diseñador de áreas del formulario para modificar un área del formulario importada, no hay ninguna manera de cambiar el modificador de un control en la ventana **Propiedades** .  

 Para habilitar el acceso a un control desde fuera del archivo de código del área del formulario, cree una propiedad en el archivo de código del área del formulario que devuelva dicho control.  

 Para obtener más información acerca de cómo crear propiedades en C#, vea [Cómo: declarar y usar propiedades de escritura de lectura &#40;C&#35; Guía de programación de&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).  

 Para obtener más información acerca de cómo crear propiedades en Visual Basic, consulte [Cómo: crear una propiedad (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).  

## <a name="see-also"></a>Vea también  
 [Instrucciones para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)   
 [Tutorial: Diseñar un área de formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)   
 [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)   
 [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)   
 [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)   
 [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)   
 [Cómo: impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Obtener acceso a la cinta en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)  
