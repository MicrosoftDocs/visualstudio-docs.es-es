---
title: "Soluciones de Word | Microsoft Docs"
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
  - "soluciones [desarrollo de Office en Visual Studio], Word"
  - "proyectos de Office [desarrollo de Office en Visual Studio], Word"
  - "complementos de nivel de aplicación [desarrollo de Office en Visual Studio], Word"
  - "Word [desarrollo de Office en Visual Studio]"
  - "proyectos [desarrollo de Office en Visual Studio], Word"
  - "Word [desarrollo de Office en Visual Studio], información sobre las soluciones de Word"
  - "soluciones de Office [desarrollo de Office en Visual Studio], Word"
  - "Word [desarrollo de Office en Visual Studio], complementos de nivel de aplicación"
  - "documentos [desarrollo de Office en Visual Studio], Word"
  - "desarrollo de Office en Visual Studio, soluciones de Word"
  - "complementos [desarrollo de Office en Visual Studio], Word"
  - "Word [desarrollo de Office en Visual Studio], personalizaciones de nivel de documento"
  - "interfaces de usuario [desarrollo de Office en Visual Studio], Word"
  - "documentos de Office [desarrollo de Office en Visual Studio], Word"
  - "personalizaciones de nivel de documento [desarrollo de Office en Visual Studio], Word"
ms.assetid: ef339ad8-1897-4a44-b588-e6004d0b6d8b
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Soluciones de Word
  Visual Studio proporciona plantillas de proyecto que puede usar para crear personalizaciones de nivel de documento y complementos de VSTO para Microsoft Office Word. Puede usar estas soluciones para automatizar Word, ampliar las características de Word y personalizar la interfaz de usuario \(IU\) de Word. Para obtener más información sobre las diferencias entre las personalizaciones de nivel de documento y los complementos VSTO, consulte [Información general sobre el desarrollo de soluciones de Office &#40;VSTO&#41;](../vsto/office-solutions-development-overview-vsto.md).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 En este tema se proporciona la información siguiente:  
  
-   [Automatizar Word](#automating).  
  
-   [Desarrollar personalizaciones de nivel de documento para Word](#doclevel).  
  
-   [Desarrollar complementos de VSTO para Word](#applevel).  
  
-   [Personalización de la interfaz de usuario de Word](#UI).  
  
##  <a name="automating"></a> Automatizar Word  
 El modelo de objetos de Word expone muchos tipos que puede usar para automatizar Word. Por ejemplo, mediante programación puede crear tablas, dar formato a documentos y establecer el texto en rangos y párrafos. Para obtener más información, consulta [Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md).  
  
 Al desarrollar soluciones de Word en Visual Studio, también puede usar *elementos host* y *controles host* en sus soluciones. Se trata de objetos que amplían algunos objetos usados habitualmente en el modelo de objetos de Word, como los objetos <xref:Microsoft.Office.Interop.Word.Document> y <xref:Microsoft.Office.Interop.Word.ContentControl>. Los objetos extendidos se comportan como los objetos de Word en los que se basan, pero agregan eventos adicionales y capacidades de enlace de datos a los objetos. Para obtener más información, consulta [Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md).  
  
##  <a name="doclevel"></a> Desarrollar personalizaciones de nivel de documento para Word  
 Una personalización de nivel de documento para Microsoft Office Word se compone de un ensamblado asociado a un documento específico. Normalmente, el ensamblado amplía el documento personalizando la interfaz de usuario y automatizando Word. A diferencia de los complementos de VSTO, que están asociados a Word en sí, la funcionalidad que implementa en una personalización está disponible únicamente cuando el documento asociado se abre en Word.  
  
 Para crear un proyecto de personalización de nivel de documento para Word, use las plantillas de proyecto de documento o de plantilla de Word en el cuadro de diálogo **Nuevo proyecto** de Visual Studio. Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obtener más información sobre el funcionamiento de las personalizaciones de nivel de documento, consulte [Arquitectura de las personalizaciones de nivel de documento](../vsto/architecture-of-document-level-customizations.md).  
  
### Modelo de programación de la personalización de Word  
 Al crear un proyecto de nivel de documento para Word, Visual Studio genera una clase, llamada `ThisDocument`, que es la base de su solución. Esta clase representa el documento asociado a la solución y proporciona un punto de partida para escribir el código.  
  
 Para obtener más información sobre la clase `ThisDocument` y otras características que pueden usarse en un proyecto de nivel de documento, consulte [Programar personalizaciones de nivel de documento](../vsto/programming-document-level-customizations.md).  
  
##  <a name="applevel"></a> Desarrollar complementos de VSTO para Word  
 Un complemento de VSTO para Microsoft Office Word está formado por un ensamblado cargado por Word. Normalmente, el ensamblado amplía Word personalizando la interfaz de usuario y automatizando Word. A diferencia de las personalizaciones de nivel de documento, que están asociadas a un documento concreto, la funcionalidad que se implementa en un complemento de VSTO no está restringida a ningún documento específico.  
  
 Para crear un proyecto de complemento de VSTO para Word, use las plantillas de proyecto de complementos de Word en el cuadro de diálogo **Nuevo proyecto** de Visual Studio. Para obtener más información, consulta [Cómo: Crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
 Para obtener información general sobre cómo funcionan los complementos de VSTO, consulte [Arquitectura de complementos de VSTO](../vsto/architecture-of-vsto-add-ins.md).  
  
### Modelo de programación de complementos de Word  
 Al crear un proyecto de complemento de VSTO para Word, Visual Studio genera una clase, denominada `ThisAddIn`, que es la base de su solución. Esta clase proporciona un punto de partida para escribir el código y expone el modelo de objetos de Word en el complemento de VSTO.  
  
 Para obtener más información sobre la clase `ThisAddIn` y otras características que puede usar en un complemento de VSTO, consulte [Programar complementos de VSTO](../vsto/programming-vsto-add-ins.md).  
  
##  <a name="UI"></a> Personalización de la interfaz de usuario de Word  
 Hay varias maneras de personalizar la interfaz de usuario de Word. Algunas opciones están disponibles para todos los tipos de proyecto, mientras que otras solo están disponibles para los complementos de VSTO o las personalizaciones de nivel de documento.  
  
### Opciones para todos los tipos de proyecto  
 En la tabla siguiente se enumeran las opciones de personalización disponibles para las personalizaciones de nivel de documento y los complementos de VSTO.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Personalizar la cinta.|[Información general sobre la cinta de opciones](../vsto/ribbon-overview.md)|  
|Agregue controles de Windows Forms o controles extendidos de Word al documento personalizado \(para las personalizaciones de nivel de documento\) o a cualquier documento abierto \(para los complementos de VSTO\).|[Cómo: Agregar controles de Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md)<br /><br /> [Cómo: Agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md)<br /><br /> [Cómo: Agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md)|  
  
### Opciones para las personalizaciones de nivel de documento  
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para las personalizaciones de nivel de documento.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Agregar un panel de acciones al documento.|[Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)<br /><br /> [Cómo: Agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)|  
|Agregar controles extendidos XMLNode y XMLNodes a la superficie del documento.|[Cómo: Agregar controles XMLNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md)<br /><br /> [Cómo: Agregar controles XMLNodes a documentos de Word](../vsto/how-to-add-xmlnodes-controls-to-word-documents.md)|  
  
### Opciones para los complementos de VSTO  
 En la siguiente tabla se enumeran las opciones de personalización disponibles únicamente para los complementos de VSTO.  
  
|Tarea|Para obtener más información|  
|-----------|----------------------------------|  
|Crear un panel de tareas personalizado.|[Paneles de tareas personalizados](../vsto/custom-task-panes.md)|  
  
### Temas relacionados  
  
|Título|Descripción|  
|------------|-----------------|  
|[Información general acerca del modelo de objetos de Word](../vsto/word-object-model-overview.md)|Ofrece una visión general de los principales tipos que proporciona el modelo de objetos de Word.|  
|[Automatizar Word con objetos extendidos](../vsto/automating-word-by-using-extended-objects.md)|Proporciona información sobre los objetos extendidos \(proporcionados por el [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)]\) que puede usar en las soluciones de Word.|  
|[Información general sobre controles de formularios Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)|Describe cómo puede agregar controles de Windows Forms a documentos de Word.|  
|[Tutorial: Crear la primera personalización en el nivel del documento para Word](../vsto/walkthrough-creating-your-first-document-level-customization-for-word.md)|Muestra cómo crear una personalización básica de nivel de documento para Word.|  
|[Tutorial: Crear el primer complemento de VSTO para Word](../vsto/walkthrough-creating-your-first-vsto-add-in-for-word.md)|Muestra cómo crear un complemento básico de VSTO para Word.|  
|[Tutorial: Agregar controles a un documento en tiempo de ejecución en un complemento de VSTO](../vsto/walkthrough-adding-controls-to-a-document-at-run-time-in-a-vsto-add-in.md)|Muestra cómo agregar un botón de Windows Forms y un <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento en tiempo de ejecución mediante un complemento de VSTO.|  
|[Desarrollo de Word 2010 en Office](http://go.microsoft.com/fwlink/?LinkId=199020)|Proporciona vínculos a artículos y documentación de referencia sobre cómo desarrollar soluciones de Word \(no específicas para el desarrollo de Office mediante Visual Studio\).|  
  
  