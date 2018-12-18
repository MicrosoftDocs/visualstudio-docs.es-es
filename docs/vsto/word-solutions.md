---
title: soluciones para Word
ms.custom: ''
ms.date: 02/02/2017
ms.technology:
- office-development
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- solutions [Office development in Visual Studio], Word
- Office projects [Office development in Visual Studio], Word
- application-level add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio]
- projects [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], about Word solutions
- Office solutions [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], application-level add-ins
- documents [Office development in Visual Studio], Word
- Office development in Visual Studio, Word solutions
- add-ins [Office development in Visual Studio], Word
- Word [Office development in Visual Studio], document-level customizations
- user interfaces [Office development in Visual Studio], Word
- Office documents [Office development in Visual Studio, Word
- document-level customizations [Office development in Visual Studio], Word
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 2b443cd985910cbb6e81ce79016193623bdeb2dd
ms.sourcegitcommit: 6944ceb7193d410a2a913ecee6f40c6e87e8a54b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/06/2018
ms.locfileid: "35674420"
---
# <a name="word-solutions"></a>soluciones para Word
  Visual Studio proporciona plantillas de proyecto que puede usar para crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Word. Puede usar estas soluciones para automatizar Word, ampliar las características de Word y personalizar la interfaz de usuario (IU) de Word. Para obtener más información sobre las diferencias entre las personalizaciones de nivel de documento y complementos VSTO, consulte [información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
> [!NOTE]  
>  ¿Está interesado en desarrollar soluciones que amplían la experiencia de Office a través de [varias plataformas](https://dev.office.com/add-in-availability)? Visite el nuevo [modelo de complementos de Office](https://dev.office.com/docs/add-ins/overview/office-add-ins). Complementos de Office tienen una superficie pequeña en comparación con las soluciones y complementos VSTO, y puede crearlas con prácticamente cualquier tecnología, como HTML5, CSS3, JavaScript y XML de programación web.  
  
 En este tema se proporciona la información siguiente:  
  
-   [Automatizar Word](#automating).  
  
-   [Desarrollar personalizaciones de nivel de documento para Word](#doclevel).  
  
-   [Desarrollar complementos VSTO para Word](#applevel).  
  
-   [Personalizar la interfaz de usuario de Word](#UI).  
  
##  <a name="automating"></a> Automatizar Word  
 El modelo de objetos de Word expone muchos tipos que puede usar para automatizar Word. Por ejemplo, mediante programación puede crear tablas, dar formato a documentos y establecer el texto en rangos y párrafos. Para obtener más información, consulte [información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
 Al desarrollar soluciones de Word en Visual Studio, también puede usar *elementos host* y *controles host* en sus soluciones. Se trata de objetos que amplían algunos objetos usados habitualmente en el modelo de objetos de Word, como los objetos <xref:Microsoft.Office.Interop.Word.Document> y <xref:Microsoft.Office.Interop.Word.ContentControl> . Los objetos extendidos se comportan como los objetos de Word en los que se basan, pero agregan eventos adicionales y capacidades de enlace de datos a los objetos. Para obtener más información, consulte [automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Desarrollar personalizaciones de nivel de documento para Word  
 Una personalización de nivel de documento para Microsoft Office Word se compone de un ensamblado asociado a un documento específico. Normalmente, el ensamblado amplía el documento personalizando la interfaz de usuario y automatizando Word. A diferencia de los complementos de VSTO, que están asociados a Word en sí, la funcionalidad que implementa en una personalización está disponible únicamente cuando el documento asociado se abre en Word.  
  
 Para crear un proyecto de personalización de nivel de documento para Word, use las plantillas de proyecto de documento o de plantilla de Word en el cuadro de diálogo **Nuevo proyecto** de Visual Studio. Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obtener más información sobre cómo funcionan las personalizaciones de nivel de documento cómo, [arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
### <a name="word-customization-programming-model"></a>Modelo de programación de la personalización de Word  
 Al crear un proyecto de nivel de documento para Word, Visual Studio genera una clase, llamada `ThisDocument`, que es la base de su solución. Esta clase representa el documento asociado a la solución y proporciona un punto de partida para escribir el código.  
  
 Para obtener más información sobre la `ThisDocument` clase y otras características que puede usar en un proyecto de nivel de documento, consulte [programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Desarrollar complementos VSTO para Word  
 Un complemento de VSTO para Microsoft Office Word está formado por un ensamblado cargado por Word. Normalmente, el ensamblado amplía Word personalizando la interfaz de usuario y automatizando Word. A diferencia de una personalización de nivel de documento, que está asociada a un documento específico, funcionalidad que se implementa en un complemento de VSTO no está restringida a ningún documento.  
  
 Para crear un proyecto de complemento de VSTO para Word, use las plantillas de proyecto de complementos de Word en el cuadro de diálogo **Nuevo proyecto** de Visual Studio. Para obtener más información, consulte [Cómo: proyectos de creación de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obtener información general sobre cómo funcionan los complementos de VSTO, consulte [Architecture of VSTO Add-ins](../vsto/architecture-of-vsto-add-ins.md).  
  
### <a name="word-add-in-programming-model"></a>Word agregar modelo de programación de  
 Al crear un proyecto de complemento de VSTO para Word, Visual Studio genera una clase, denominada `ThisAddIn`, que es la base de su solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Word en el complemento de VSTO.  
  
 Para obtener más información sobre la `ThisAddIn` clase y otras características que puede usar en un complemento de VSTO, consulte [complementos VSTO de programa](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Personalizar la interfaz de usuario de Word  
 Hay varias maneras de personalizar la interfaz de usuario de Word. Algunas opciones están disponibles para todos los tipos de proyecto, mientras que otras solo están disponibles para los complementos de VSTO o las personalizaciones de nivel de documento.  
  
### <a name="options-for-all-project-types"></a>Opciones para todos los tipos de proyecto  
 En la tabla siguiente se enumeran las opciones de personalización disponibles para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Personalizar la cinta.|[Información general de la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregue controles de Windows Forms o controles extendidos de Word al documento personalizado (para las personalizaciones de nivel de documento) o a cualquier documento abierto (para los complementos de VSTO).|[Cómo: agregar controles de formularios Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Cómo: agregar controles bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### <a name="options-for-document-level-customizations"></a>Opciones para las personalizaciones de nivel de documento  
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para las personalizaciones de nivel de documento.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Agregar un panel de acciones al documento.|[Información general sobre el panel de acciones](../vsto/actions-pane-overview.md)<br /><br /> [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Agregar controles extendidos XMLNode y XMLNodes a la superficie del documento.|[Cómo: agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Cómo: agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### <a name="options-for-vsto-add-ins"></a>Opciones para los complementos de VSTO  
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para los complementos de VSTO.  
  
|Tarea|Para obtener más información|  
|----------|--------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
  
### <a name="related-topics"></a>Temas relacionados  
  
|Título|Descripción|  
|-----------|-----------------|  
|[Información general sobre el modelo de objetos de Word](../vsto/word-object-model-overview.md)|Ofrece una visión general de los principales tipos que proporciona el modelo de objetos de Word.|  
|[Automatizar Word usando objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)|Proporciona información sobre los objetos extendidos (proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]) que puede usar en las soluciones de Word.|  
|[Controles de Windows Forms en información general sobre documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Describe cómo puede agregar controles de Windows Forms a documentos de Word.|  
|[Tutorial: Crear la primera personalización de nivel de documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Muestra cómo crear una personalización básica de nivel de documento para Word.|  
|[Tutorial: Crear el primer complemento VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Muestra cómo crear un complemento básico de VSTO para Word.|  
|[Tutorial: Agregar controles a un documento en tiempo de ejecución en un complemento de VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Muestra cómo agregar un botón de Windows Forms y un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento en tiempo de ejecución mediante un complemento de VSTO.|  
|[Word 2010 en el desarrollo de Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Proporciona vínculos a artículos y documentación de referencia sobre cómo desarrollar soluciones de Word (no específicas para el desarrollo de Office mediante Visual Studio).|  
  
  