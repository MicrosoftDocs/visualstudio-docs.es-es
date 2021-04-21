---
title: 'Cómo: Proteger hojas de cálculo mediante programación'
description: Obtenga información sobre cómo puede usar la característica de protección de Microsoft Excel para evitar que los usuarios y el código modifiquen objetos en una hoja de cálculo.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- protection, adding to worksheets
- documents [Office development in Visual Studio], document protection
- document protection, adding to worksheets
- worksheets, protecting
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 31c0184cbf8f29db6d33d135cf295f8277b55f2e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/21/2021
ms.locfileid: "107827106"
---
# <a name="how-to-programmatically-protect-worksheets"></a>Cómo: Proteger hojas de cálculo mediante programación
  La característica de protección de Microsoft Office Excel ayuda a evitar que los usuarios y el código modifiquen los objetos de una hoja de cálculo. De forma predeterminada, todas las celdas se bloquean después de activar la protección.

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

 En las personalizaciones de nivel de documento, puede proteger hojas de cálculo usando el diseñador de Excel. También puede proteger una hoja de cálculo mediante programación en tiempo de ejecución en cualquier tipo de proyecto.

> [!NOTE]
> No puede agregar controles de Windows Forms a las áreas de una hoja de cálculo que están protegidas.

## <a name="use-the-designer"></a>Uso del diseñador

### <a name="to-protect-a-worksheet-in-the-designer"></a>Para proteger una hoja de cálculo en el diseñador

1. En el **grupo Cambios** de la **pestaña Revisar** , haga clic en **Proteger hoja**.

    Aparece **el cuadro de diálogo** Proteger hoja. Puede establecer una contraseña y, si lo desea, especificar algunas acciones que los usuarios pueden realizar en la hoja de cálculo, como, por ejemplo, dar formato a las celdas o insertar filas.

   También puede permitir a los usuarios editar determinados rangos en hojas de cálculo protegidas.

### <a name="to-allow-editing-in-specific-ranges"></a>Para permitir la modificación de rangos específicos

1. En el **grupo Cambios** de la **pestaña Revisar** , haga clic en Permitir a los usuarios **editar intervalos.**

     Aparece **el cuadro de diálogo Permitir** a los usuarios editar intervalos . Puede especificar rangos que se desbloqueen mediante una contraseña y usuarios que pueden editar rangos sin contraseña.

## <a name="use-code-at-run-time"></a>Uso de código en tiempo de ejecución
 El siguiente código establece la contraseña (mediante la variable getPasswordFromUser, que contiene una contraseña obtenida del usuario) y solo permite la ordenación.

### <a name="to-protect-a-worksheet-by-using-code-in-a-document-level-customization"></a>Para proteger una hoja de cálculo mediante código en una personalización de nivel de documento

1. Llame al método <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A> de la hoja de cálculo. En este ejemplo se da por supuesto que está trabajando con una hoja de cálculo denominada `Sheet1`.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs" id="Snippet27":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb" id="Snippet27":::

### <a name="to-protect-a-worksheet-by-using-code-in-a-vsto-add-in"></a>Para proteger una hoja de cálculo mediante código en un complemento de VSTO

1. Llame al método <xref:Microsoft.Office.Interop.Excel._Worksheet.Protect%2A> de la hoja de cálculo activa.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs" id="Snippet17":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb" id="Snippet17":::

## <a name="see-also"></a>Consulte también
- [Trabajar con hojas de cálculo](../vsto/working-with-worksheets.md)
- [Cómo: Quitar la protección de hojas de cálculo mediante programación](../vsto/how-to-programmatically-remove-protection-from-worksheets.md)
- [Cómo: Proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md)
- [Cómo: Ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md)
- [Introducción a los elementos host y los controles host](../vsto/host-items-and-host-controls-overview.md)
- [Elemento host de hoja de cálculo](../vsto/worksheet-host-item.md)
- [Acceso global a objetos en proyectos de Office](../vsto/global-access-to-objects-in-office-projects.md)
- [Parámetros opcionales en soluciones de Office](../vsto/optional-parameters-in-office-solutions.md)
