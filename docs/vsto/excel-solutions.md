---
title: soluciones de Excel
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 8e2c6e25c3acdfb4c90eb0ba74d66670be339588
ms.sourcegitcommit: 1466ac0f49ebf7448ea4507ae3f79acb25d51d3e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/22/2018
---
# <a name="excel-solutions"></a>soluciones de Excel
  Visual Studio proporciona plantillas de proyecto que puede usar para crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Excel. Puede usar estas soluciones para automatizar Excel, ampliar las características de Excel y personalizar la interfaz de usuario (UI) de Excel. Para obtener más información acerca de las diferencias entre las personalizaciones de nivel de documento y complementos VSTO, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en el desarrollo de soluciones que amplían la experiencia de Office en [varias plataformas](https://dev.office.com/add-in-availability)? Visite la nueva [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede compilarlas mediante prácticamente cualquier tecnología, como HTML5, JavaScript, CSS3 y XML de programación web.  
  
 En este tema se proporciona la información siguiente:  
  
-   [Automatizar Excel](#automating).  
  
-   [Desarrollar personalizaciones de nivel de documento para Excel](#doclevel).  
  
-   [Desarrollar complementos VSTO para Excel](#applevel).  
  
-   [Personalizar la interfaz de usuario de Excel](#UI).  
  
##  <a name="automating"></a> Automatizar Excel  
 El modelo de objetos de Excel expone muchos tipos que puede usar para automatizar Excel. Por ejemplo, mediante programación puede crear gráficos, dar formato a hojas de cálculo y establecer los valores de rangos y celdas. Para obtener más información, consulte [información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md).  
  
 Al desarrollar soluciones de Excel en Visual Studio, también puede usar *elementos host* y *controles host* en sus soluciones. Se trata de objetos que amplían algunos objetos usados habitualmente en el modelo de objetos de Excel, como los objetos <xref:Microsoft.Office.Interop.Excel.Worksheet> y <xref:Microsoft.Office.Interop.Excel.Range> . Los objetos extendidos se comportan como los objetos de Excel en los que se basan, pero agregan eventos adicionales y capacidades de enlace de datos a los objetos. Para obtener más información, consulte [automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Desarrollar personalizaciones de nivel de documento para Excel  
 Una personalización de nivel de documento para Microsoft Office Excel se compone de un ensamblado asociado a un libro específico. Normalmente, el ensamblado amplía el libro personalizando la interfaz de usuario y automatizando Excel. A diferencia de los complementos de VSTO, que están asociados a Excel en sí, la funcionalidad que implementa en una personalización está disponible únicamente cuando el libro asociado se abre en Excel.  
  
 Para crear un proyecto de personalización de nivel de documento para Excel, use el libro de Excel o plantillas de proyecto de plantilla de Excel en el **nuevo proyecto** cuadro de diálogo de Visual Studio. Para obtener más información, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obtener más información acerca de cómo funcionan las personalizaciones de nivel de documento cómo, consulte [arquitectura de las personalizaciones de nivel de documento de](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="excel-customization-programming-model"></a>Modelo de programación de personalización de Excel  
 Al crear un proyecto de nivel de documento para Excel, Visual Studio genera varias clases, que son la base de su solución: `ThisWorkbook`, `Sheet1`, `Sheet2`y `Sheet3`. Estas clases representan el libro y las hojas de cálculo que están asociados a su solución y proporcionan un punto de partida para escribir el código.  
  
 Para obtener más información sobre estas clases generadas y otras características que puede usar en un proyecto de nivel de documento, consulte [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Desarrollar complementos VSTO para Excel  
 Un complemento de VSTO para Microsoft Office Excel está formado por un ensamblado cargado por Excel. Normalmente, el ensamblado amplía Excel personalizando la interfaz de usuario y automatizando Excel. A diferencia de las personalizaciones de nivel de documento, que están asociadas a un libro concreto, la funcionalidad que implemente en un complemento VSTO no está restringida a ningún libro específico.  
  
 Para crear un proyecto de complemento de VSTO para Excel, use el libro de Excel o plantillas de proyecto de plantilla de Excel en el **nuevo proyecto** cuadro de diálogo de Visual Studio. Para obtener más información, consulte [Cómo: proyectos de Office crear en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obtener información general sobre cómo funcionan los complementos de VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
 ![vínculo a vídeo](../vsto/media/playvideo.gif "vínculo a vídeo") para una demostración en vídeo relacionada, vea [¿cómo automatizar PowerPoint desde un complemento de Excel?](http://go.microsoft.com/fwlink/?LinkID=130300).  
  
### <a name="excel-add-in-programming-model"></a>Modelo de programación de complementos de Excel  
 Al crear un proyecto de complemento VSTO de Excel, Visual Studio crea una clase denominada `ThisAddIn`, que es la base de la solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Excel en el complemento VSTO.  
  
 Para obtener más información sobre la `ThisAddIn` clase y otras características de Visual Studio que puede usar en un complemento de VSTO, consulte [los complementos de VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Personalizar la interfaz de usuario de Excel  
 Hay varias maneras de personalizar la interfaz de usuario de Excel. Algunas opciones están disponibles para todos los tipos de proyecto, mientras que otras solo están disponibles para los complementos de VSTO o las personalizaciones de nivel de documento.  
  
### <a name="options-for-all-project-types"></a>Opciones para todos los tipos de proyecto  
 En la tabla siguiente se enumeran las opciones de personalización disponibles para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Personalizar la cinta.|[Información general de la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregar controles de Windows Forms o controles extendidos de Excel a una hoja de cálculo en el libro personalizado para una personalización de nivel de documento o a cualquier libro abierto para un complemento de VSTO.|[Cómo: agregar controles de Windows forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Cómo: agregar controles Chart a hojas de cálculo](../vsto/how-to-add-chart-controls-to-worksheets.md)<br /><br /> [Cómo: agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md)<br /><br /> [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opciones para las personalizaciones de nivel de documento  
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para las personalizaciones de nivel de documento.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Agregar un panel de acciones al libro.|[Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)<br /><br /> [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Agregue controles de rango extendido que se asignan a nodos XML a una hoja de cálculo.|[Cómo: agregar controles XMLMappedRange a hojas de cálculo](../vsto/how-to-add-xmlmappedrange-controls-to-worksheets.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opciones para los complementos de VSTO  
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para los complementos de VSTO.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Temas relacionados  
|Título|Descripción|  
|-----------|-----------------|  
|[Información general sobre el modelo de objetos de Excel](../vsto/excel-object-model-overview.md)|Ofrece una visión general de los principales tipos que proporciona el modelo de objetos de Excel.|  
|[Automatizar Excel usando objetos extendidos](../vsto/automating-excel-by-using-extended-objects.md)|Proporciona información acerca de los objetos extendidos (proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que puede usar en soluciones de Excel.|  
|[Globalización y localización de soluciones de Excel](../vsto/globalization-and-localization-of-excel-solutions.md)|Contiene información sobre consideraciones especiales para las soluciones de Excel que se vayan a ejecutar en equipos que tengan una configuración distinta del inglés para Windows.|  
|[Controles de formularios Windows Forms en información general acerca de documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Describe cómo puede agregar controles de Windows Forms a hojas de cálculo de Excel.|  
|[Tutorial: Crear la primera personalización de nivel de documento para Excel](../vsto/walkthrough-creating-your-first-document-level-customization-for-excel.md)|Muestra cómo crear una personalización básica de nivel de documento para Excel.|  
|[Tutorial: Crear el primer complemento de VSTO para Excel](../vsto/walkthrough-creating-your-first-vsto-add-in-for-excel.md)|Muestra cómo crear un complemento básico de VSTO para Excel.|  
|[Tutorial: Agregar controles a una hoja de cálculo en tiempo de ejecución en el proyecto de complemento de VSTO](../vsto/walkthrough-adding-controls-to-a-worksheet-at-run-time-in-vsto-add-in-project.md)|Muestra cómo agregar un botón de formularios Windows Forms, un <xref:Microsoft.Office.Tools.Excel.NamedRange>y un <xref:Microsoft.Office.Tools.Excel.ListObject> a una hoja de cálculo en tiempo de ejecución mediante el uso de un complemento de VSTO.|
|[Entender la generación conjunta y complementos](./understanding-coauthoring-and-addins.md)|Describe los ajustes que necesite realizar en sus soluciones para dar cabida a co-autoría.|  
|[Excel 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199011)|Proporciona vínculos a artículos y documentación de referencia sobre el desarrollo de soluciones de Excel. Estos no son específicos para el desarrollo de Office mediante Visual Studio.|  
  
  