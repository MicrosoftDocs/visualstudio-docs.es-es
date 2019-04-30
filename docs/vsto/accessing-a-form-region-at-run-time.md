---
title: Obtener acceso a un área de formulario en tiempo de ejecución
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Inspectors [Office development in Visual Studio]
- Explorers [Office development in Visual Studio]
- form regions [Office development in Visual Studio], accessing at runtime
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: eed4d9dee7cc6c7de387d590662c47d90a99a2ab
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63001153"
---
# <a name="access-a-form-region-at-runtime"></a>Obtener acceso a un área de formulario en tiempo de ejecución

|Se aplica a|
|----------------|
|La información de este tema solamente se aplica a los siguientes tipos de proyectos y versiones de Microsoft Office. Para obtener más información, consulte [características disponibles por tipo de aplicación y el proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md).<br /><br /> **Tipo de proyecto**<br /><br /> : Proyectos de complemento de VSTO<br /><br /> **Versión de Microsoft Office**<br /><br /> -   [!INCLUDE[Outlook_14_short](../vsto/includes/outlook-14-short-md.md)]|

 Utilice la clase `Globals` para acceder a áreas del formulario desde cualquier lugar dentro del proyecto de Outlook. Para obtener más información sobre la `Globals` de clases, vea [acceso Global a objetos en los proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md).

 [!INCLUDE[appliesto_olkallapp](../vsto/includes/appliesto-olkallapp-md.md)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-inspector-window"></a>Áreas de formulario de Access que aparecen en una ventana específica del Inspector de Outlook
 Para acceder a todas las áreas del formulario que aparecen en un Inspector de Outlook concreto, llame a la propiedad `FormRegions` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Inspector> que represente el Inspector.

 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en el Inspector que tiene actualmente el foco. Después, este ejemplo accede a un área del formulario de la colección denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#2](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#2)]
 [!code-csharp[Trin_Outlook_FR_Access#2](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#2)]

## <a name="access-form-regions-that-appear-in-a-specific-outlook-explorer-window"></a>Áreas de formulario de Access que aparecen en una ventana específica del explorador de Outlook
 Para acceder a todas las áreas del formulario que aparecen en un Explorador de Outlook concreto, llame a la propiedad `FormRegions` de la clase `Globals` y pase un objeto <xref:Microsoft.Office.Interop.Outlook.Explorer> que represente el explorador.

 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en el explorador que tiene actualmente el foco. Después, este ejemplo accede a un área del formulario de la colección denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#3](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#3)]
 [!code-csharp[Trin_Outlook_FR_Access#3](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#3)]

## <a name="access-all-form-regions"></a>Obtener acceso a todas las áreas de formulario
 Para acceder a todas las áreas del formulario que aparecen en todos los exploradores e inspectores, llame a la propiedad `FormRegions` de la clase `Globals` .

 El ejemplo siguiente obtiene la colección de áreas del formulario que aparecen en todos los exploradores e inspectores. En este ejemplo accede entonces a un área del formulario denominada `formRegion1` y establece el texto que aparece en un cuadro de texto como `Hello World`.

 [!code-vb[Trin_Outlook_FR_Access#1](../vsto/codesnippet/VisualBasic/Trin_Outlook_FR_Access_O12/ThisAddIn.vb#1)]
 [!code-csharp[Trin_Outlook_FR_Access#1](../vsto/codesnippet/CSharp/Trin_Outlook_FR_Access_O12/ThisAddIn.cs#1)]

## <a name="access-controls-on-a-form-region"></a>Controles de acceso en un área de formulario
 Para acceder a los controles en un área de formulario mediante la clase `Globals` , debe conseguir que los controles sean accesibles para el código de fuera del archivo de código del área del formulario.

### <a name="form-regions-designed-in-the-form-region-designer"></a>Áreas de formulario diseñadas en el Diseñador de áreas de formulario
 En C#, cambie el modificador de cada control al que quiera tener acceso. Para ello, seleccione cada uno de los controles en el diseñador de áreas del formulario y cambie la propiedad **Modificadores** a **Internos** o **Públicos** en la ventana **Propiedades** . Por ejemplo, si cambia la propiedad **Modificador** de `textBox1` a **Interno**, puede acceder a `textBox1` si escribe `Globals.FormRegions.FormRegion1.textBox1`.

 En Visual Basic no es necesario cambiar el modificador.

### <a name="imported-form-regions"></a>Áreas de formulario importada
 Al importar un área del formulario que se diseñó en Outlook, el modificador de acceso de cada control en el área del formulario pasa a ser privado. Como no se puede usar el diseñador de áreas del formulario para modificar un área del formulario importada, no hay ninguna manera de cambiar el modificador de un control en la ventana **Propiedades** .

 Para habilitar el acceso a un control desde fuera del archivo de código del área del formulario, cree una propiedad en el archivo de código del área del formulario que devuelva dicho control.

 Para obtener más información acerca de cómo crear propiedades en C#, vea [Cómo: Declarar y usar leer escribir propiedades &#40;C&#35; Guía de programación&#41;](/dotnet/csharp/programming-guide/classes-and-structs/how-to-declare-and-use-read-write-properties).

 Para obtener más información sobre cómo crear propiedades en Visual Basic, vea [Cómo: Crear una propiedad (Visual Basic)](/dotnet/visual-basic/programming-guide/language-features/procedures/how-to-create-a-property).

## <a name="see-also"></a>Vea también
- [Directrices para crear áreas de formulario de Outlook](../vsto/guidelines-for-creating-outlook-form-regions.md)
- [Tutorial: Diseñar un formulario de Outlook](../vsto/walkthrough-designing-an-outlook-form-region.md)
- [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
- [Acciones personalizadas en áreas de formulario de Outlook](../vsto/custom-actions-in-outlook-form-regions.md)
- [Asociar un área de formulario a una clase de mensaje de Outlook](../vsto/associating-a-form-region-with-an-outlook-message-class.md)
- [Tutorial: Importar un área de formulario diseñada en Outlook](../vsto/walkthrough-importing-a-form-region-that-is-designed-in-outlook.md)
- [Cómo: Impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Obtener acceso a la cinta de opciones en tiempo de ejecución](../vsto/accessing-the-ribbon-at-run-time.md)
