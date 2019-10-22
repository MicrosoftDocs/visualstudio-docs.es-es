---
title: soluciones de Excel
ms.date: 08/14/2019
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- application-level add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], application-level add-ins
- Office solutions [Office development in Visual Studio], Excel
- solutions [Office development in Visual Studio], Excel
- add-ins [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], about Excel solutions
- Excel [Office development in Visual Studio]
- documents [Office development in Visual Studio], Excel
- Office documents [Office development in Visual Studio, Excel
- projects [Office development in Visual Studio], Excel
- Excel [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Excel
- Office development in Visual Studio, Excel solutions
- document-level customizations [Office development in Visual Studio], Excel
- Office projects [Office development in Visual Studio], Excel
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 532689afe4e07c3151be6eac923f2b591aa34f46
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/25/2019
ms.locfileid: "71253622"
---
# <a name="excel-solutions"></a>soluciones de Excel
  Visual Studio proporciona plantillas de proyecto que puede usar para crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Excel. Puede usar estas soluciones para automatizar Excel, ampliar las características de Excel y personalizar la interfaz de usuario (UI) de Excel. Para obtener más información sobre las diferencias entre las personalizaciones de nivel de documento y los complementos de VSTO, consulte [ &#40;información&#41;general sobre el desarrollo de soluciones de Office VSTO](../vsto/office-solutions-development-overview-vsto.md).

 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]

[!include[Add-ins note](includes/addinsnote.md)]

 En este tema se proporciona la información siguiente:

- [Automatizar Excel](#automating).

- [Desarrollar personalizaciones de nivel de documento para Excel](#doclevel).

- [Desarrollar complementos de VSTO para Excel](#applevel).

- [Personalizar la interfaz de usuario de Excel](#UI).

## <a name="automating"></a>Automatizar Excel
 El modelo de objetos de Excel expone muchos tipos que puede usar para automatizar Excel. Por ejemplo, mediante programación puede crear gráficos, dar formato a hojas de cálculo y establecer los valores de rangos y celdas. Para obtener más información, vea [información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).

 Al desarrollar soluciones de Excel en Visual Studio, también puede usar *elementos host* y *controles host* en sus soluciones. Se trata de objetos que amplían algunos objetos usados habitualmente en el modelo de objetos de Excel, como los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> y <xref:Microsoft.Office.Interop.Excel.Range> . Los objetos extendidos se comportan como los objetos de Excel en los que se basan, pero agregan eventos adicionales y capacidades de enlace de datos a los objetos. Para obtener más información, vea [automatizar Excel con objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).

## <a name="doclevel"></a>Desarrollar personalizaciones de nivel de documento para Excel
 Una personalización de nivel de documento para Microsoft Office Excel se compone de un ensamblado asociado a un libro específico. Normalmente, el ensamblado amplía el libro personalizando la interfaz de usuario y automatizando Excel. A diferencia de los complementos de VSTO, que están asociados a Excel en sí, la funcionalidad que implementa en una personalización está disponible únicamente cuando el libro asociado se abre en Excel.

 Para crear un proyecto de personalización de nivel de documento para Excel, use las plantillas de proyecto de libro de Excel o de plantilla de Excel en el cuadro de diálogo **nuevo proyecto** de Visual Studio. Para obtener más información, vea [Cómo: Cree proyectos de Office en Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

 Para obtener más información sobre cómo funcionan las personalizaciones de nivel de documento, vea [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).

### <a name="excel-customization-programming-model"></a>Modelo de programación de la personalización de Excel
 Al crear un proyecto de nivel de documento para Excel, Visual Studio genera varias clases, que son la base de su solución: `ThisWorkbook`, `Sheet1`, `Sheet2`y `Sheet3`. Estas clases representan el libro y las hojas de cálculo que están asociados a su solución y proporcionan un punto de partida para escribir el código.

 Para obtener más información sobre estas clases generadas y otras características que puede usar en un proyecto de nivel de documento, consulte [Personalización de nivel de documento de programa](../vsto/programming-document-level-customizations.md).

## <a name="applevel"></a>Desarrollo de complementos de VSTO para Excel
 Un complemento de VSTO para Microsoft Office Excel está formado por un ensamblado cargado por Excel. Normalmente, el ensamblado amplía Excel personalizando la interfaz de usuario y automatizando Excel. A diferencia de las personalizaciones de nivel de documento, que están asociadas a un libro concreto, la funcionalidad que implementa en un complemento de VSTO no está restringida a ningún libro individual.

 Para crear un proyecto de complemento de VSTO para Excel, use las plantillas de proyecto de libro de Excel o de plantilla de Excel en el cuadro de diálogo **nuevo proyecto** de Visual Studio. Para obtener más información, vea [Cómo: Cree proyectos de Office en Visual](../vsto/how-to-create-office-projects-in-visual-studio.md)Studio.

 Para obtener información general sobre cómo funcionan los complementos de VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).

### <a name="excel-add-in-programming-model"></a>Modelo de programación de complementos de Excel
 Al crear un proyecto de complemento VSTO de Excel, Visual Studio crea una clase denominada `ThisAddIn`, que es la base de la solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Excel en el complemento VSTO.

 Para obtener más información sobre `ThisAddIn` la clase y otras características de Visual Studio que puede usar en un complemento de VSTO, consulte [Complementos de VSTO de programas](../vsto/programming-vsto-add-ins.md).

## <a name="UI"></a>Personalización de la interfaz de usuario de Excel
 Hay varias maneras de personalizar la interfaz de usuario de Excel. Algunas opciones están disponibles para todos los tipos de proyecto, mientras que otras solo están disponibles para los complementos de VSTO o las personalizaciones de nivel de documento.

### <a name="options-for-all-project-types"></a>Opciones para todos los tipos de proyecto
 En la tabla siguiente se enumeran las opciones de personalización disponibles para las personalizaciones de nivel de documento y los complementos de VSTO.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Personalizar la cinta.|[Información general sobre la cinta](../vsto/ribbon-overview.md)|
|Agregar controles de Windows Forms o controles extendidos de Excel a una hoja de cálculo en el libro personalizado para una personalización de nivel de documento o a cualquier libro abierto para un complemento de VSTO.|[Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Cómo: Agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Cómo: Agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Cómo: Agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|

### <a name="options-for-document-level-customizations"></a>Opciones para las personalizaciones de nivel de documento
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para las personalizaciones de nivel de documento.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Agregar un panel de acciones al libro.|[Información general del panel de acciones](../vsto/actions-pane-overview.md)<br /><br /> [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|
|Agregue controles de rango extendido que se asignan a nodos XML a una hoja de cálculo.|[Cómo: Agregar controles XmlMappedRange (a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|

### <a name="options-for-vsto-add-ins"></a>Opciones para los complementos de VSTO
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para los complementos de VSTO.

|Tarea|Para obtener más información|
|----------|--------------------------|
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|

### <a name="related-topics"></a>Temas relacionados

| Título | Descripción |
| - | - |
| [Información general del modelo de objetos de Excel](../vsto/excel-object-model-overview.md) | Ofrece una visión general de los principales tipos que proporciona el modelo de objetos de Excel. |
| [Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md) | Proporciona información acerca de los objetos extendidos (proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que puede usar en soluciones de Excel. |
| [Globalización y localización de las soluciones de Excel](../vsto/globalization-and-localization-of-excel-solutions.md) | Contiene información sobre consideraciones especiales para las soluciones de Excel que se vayan a ejecutar en equipos que tengan una configuración distinta del inglés para Windows. |
| [Información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md) | Describe cómo puede agregar controles de Windows Forms a hojas de cálculo de Excel. |
| [Tutorial: Crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md) | Muestra cómo crear una personalización básica de nivel de documento para Excel. |
| [Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md) | Muestra cómo crear un complemento básico de VSTO para Excel. |
| [Tutorial: Agregar controles a una hoja de cálculo en tiempo de ejecución en el proyecto de complemento de VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md) | Muestra cómo agregar un botón de Windows Forms, un <xref:Microsoft.Office.Tools.Excel.NamedRange>y un <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo en tiempo de ejecución mediante un complemento de VSTO. |
| [Descripción de los complementos y la co-autoría](./understanding-coauthoring-and-addins.md) | Describe los ajustes que es posible que tenga que realizar en sus soluciones para dar cabida a la coautoría. |
| [Excel 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199011) | Proporciona vínculos a artículos y documentación de referencia sobre el desarrollo de soluciones de Excel. Estos no son específicos para el desarrollo de Office mediante Visual Studio. |
