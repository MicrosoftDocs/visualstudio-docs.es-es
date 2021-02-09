---
title: Tareas comunes en la programación de Office
description: Obtenga información sobre cómo puede programar con los datos en una personalización de nivel de documento sin tener que usar el modelo de objetos de Microsoft Office Word u Office Excel.
ms.custom: SEO-VS-2020SS
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, getting started
- FAQs (frequently asked questions) [Office development in Visual Studio]
- Office development in Visual Studio, frequently asked questions
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 67b09d3881dcde1d404b7ff0c1096ced1ecb50ea
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99910610"
---
# <a name="common-tasks-in-office-programming"></a>Tareas comunes en la programación de Office
  Este tema está diseñado para ayudarle a encontrar las respuestas a las siguientes categorías de preguntas comunes sobre la programación de soluciones de Office mediante Visual Studio.

- [Configuración y tareas generales](#projects).

- [Tareas de personalización](#ui)de la interfaz de usuario.

- [Tareas de automatización de Excel](#excel).

- [Tareas de automatización de Word](#word).

- [Tareas de datos](#data).

- [Tareas de administración de documentos de servidor](#server).

- [Tareas de seguridad](#security).

- [Tareas de implementación](#deployment).

## <a name="setup-and-general-tasks"></a><a name="projects"></a> Configuración y tareas generales

- [Cómo: crear proyectos de Office en Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).

- [Cómo: actualizar soluciones de Office](/previous-versions/4bez6837(v=vs.140)).

- [Cómo: Instalar ensamblados de interoperabilidad primarios de Office](../vsto/how-to-install-office-primary-interop-assemblies.md).

- [Cómo: dirigirse a aplicaciones de Office a través de ensamblados de interoperabilidad primarios](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md).

- [Cómo: crear controladores de eventos en proyectos de Office](../vsto/how-to-create-event-handlers-in-office-projects.md).

- [Cómo: abrir soluciones de Office sin ejecutar código](../vsto/how-to-open-office-solutions-without-running-code.md).

- [Cómo: configurar la información de configuración de una solución de Office](../vsto/how-to-set-up-configuration-information-for-an-office-solution.md).

- [Cómo: Mostrar la pestaña programador en la cinta de opciones](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

- [Cómo: Mostrar errores de la interfaz de usuario de complementos](../vsto/how-to-show-add-in-user-interface-errors.md).

## <a name="user-interface-customization-tasks"></a><a name="ui"></a> Tareas de personalización de la interfaz de usuario

### <a name="controls-on-documents-and-worksheets"></a>Controles en documentos y hojas de cálculo

- [Cómo: agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Cómo: agregar controles NamedRange a hojas de cálculo](../vsto/how-to-add-namedrange-controls-to-worksheets.md).

- [Cómo: agregar controles ListObject a hojas de cálculo](../vsto/how-to-add-listobject-controls-to-worksheets.md).

- [Cómo: agregar controles Windows Forms a documentos de Office](../vsto/how-to-add-windows-forms-controls-to-office-documents.md).

- [Cómo: agregar controles de contenido a documentos de Word](../vsto/how-to-add-content-controls-to-word-documents.md).

- [Cómo: agregar controles Bookmark a documentos de Word](../vsto/how-to-add-bookmark-controls-to-word-documents.md).

### <a name="task-panes-in-document-level-customizations"></a>Paneles de tareas en personalizaciones de nivel de documento

- [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

### <a name="task-panes-in-vsto-add-ins"></a>Paneles de tareas en complementos de VSTO

- [Cómo: agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

### <a name="ribbon-customizations"></a>Personalizaciones de la cinta

- [Cómo: empezar a personalizar la cinta de opciones](../vsto/how-to-get-started-customizing-the-ribbon.md).

- [Cómo: cambiar la posición de una pestaña en la cinta de opciones](../vsto/how-to-change-the-position-of-a-tab-on-the-ribbon.md).

- [Cómo: personalizar una pestaña integrada](../vsto/how-to-customize-a-built-in-tab.md).

- [Cómo: agregar controles a la vista Backstage](../vsto/how-to-add-controls-to-the-backstage-view.md).

- [Cómo: Exportar una cinta desde el diseñador de la cinta a XML de la cinta](../vsto/how-to-export-a-ribbon-from-the-ribbon-designer-to-ribbon-xml.md).

### <a name="outlook-form-regions"></a>Áreas de formulario de Outlook

- [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

- [Cómo: impedir que Outlook muestre un área de formulario](../vsto/how-to-prevent-outlook-from-displaying-a-form-region.md).

### <a name="custom-menus"></a>Menús personalizados

- [Cómo: agregar comandos a menús contextuales](../vsto/how-to-add-commands-to-shortcut-menus.md).

## <a name="excel-automation-tasks"></a><a name="excel"></a> Tareas de automatización de Excel

- [Cómo: mostrar una cadena en una celda de una hoja de cálculo mediante programación](../vsto/how-to-programmatically-display-a-string-in-a-worksheet-cell.md).

- [Cómo: crear nuevos libros mediante programación](../vsto/how-to-programmatically-create-new-workbooks.md).

- [Cómo: abrir libros mediante programación](../vsto/how-to-programmatically-open-workbooks.md).

- [Cómo: guardar libros mediante programación](../vsto/how-to-programmatically-save-workbooks.md).

- [Cómo: cerrar libros mediante programación](../vsto/how-to-programmatically-close-workbooks.md).

- [Cómo: agregar nuevas hojas de cálculo a libros mediante programación](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md).

- [Cómo: ocultar hojas de cálculo mediante programación](../vsto/how-to-programmatically-hide-worksheets.md).

- [Cómo: trasladar hojas de cálculo dentro de libros mediante programación](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md).

- [Cómo: proteger libros mediante programación](../vsto/how-to-programmatically-protect-workbooks.md).

- [Cómo: hacer referencia a intervalos de hojas de cálculo mediante programación en el código](../vsto/how-to-programmatically-refer-to-worksheet-ranges-in-code.md).

- [Cómo: aplicar estilos a rangos de libros mediante programación](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md).

- [Cómo: cambiar el formato en filas de hojas de cálculo que contienen celdas seleccionadas mediante programación](../vsto/how-to-programmatically-change-formatting-in-worksheet-rows-containing-selected-cells.md).

- [Cómo: buscar texto en rangos de hojas de cálculo mediante programación](../vsto/how-to-programmatically-search-for-text-in-worksheet-ranges.md).

- [Cómo: imprimir hojas de cálculo mediante programación](../vsto/how-to-programmatically-print-worksheets.md).

- [Cómo: ejecutar cálculos de Excel mediante programación](../vsto/how-to-programmatically-run-excel-calculations-programmatically.md).

- [Cómo: ordenar datos en hojas de cálculo mediante programación](../vsto/how-to-programmatically-sort-data-in-worksheets.md).

## <a name="word-automation-tasks"></a><a name="word"></a> Tareas de automatización de Word

- [Cómo: crear nuevos documentos mediante programación](../vsto/how-to-programmatically-create-new-documents.md).

- [Cómo: abrir documentos existentes mediante programación](../vsto/how-to-programmatically-open-existing-documents.md).

- [Cómo: guardar documentos mediante programación](../vsto/how-to-programmatically-save-documents.md).

- [Cómo: cerrar documentos mediante programación](../vsto/how-to-programmatically-close-documents.md).

- [Cómo: insertar texto en documentos de Word mediante programación](../vsto/how-to-programmatically-insert-text-into-word-documents.md).

- [Cómo: definir y seleccionar intervalos en documentos mediante programación](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)

- [Cómo: restablecer intervalos en documentos de Word mediante programación](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md).

- [Cómo: dar formato al texto en documentos mediante programación](../vsto/how-to-programmatically-format-text-in-documents.md).

- [Cómo: agregar controles XmlNode a documentos de Word](../vsto/how-to-add-xmlnode-controls-to-word-documents.md).

- [Cómo: actualizar texto de marcador mediante programación](../vsto/how-to-programmatically-update-bookmark-text.md).

- [Cómo: buscar y reemplazar texto en documentos mediante programación](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md).

- [Cómo: imprimir documentos mediante programación](../vsto/how-to-programmatically-print-documents.md).

- [Cómo: crear tablas de Word mediante programación](../vsto/how-to-programmatically-create-word-tables.md).

- [Cómo: Agregar filas y columnas a tablas de Word mediante programación](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md).

- [Cómo: recuento de caracteres en documentos mediante programación](../vsto/how-to-programmatically-count-characters-in-documents.md)

## <a name="data-tasks"></a><a name="data"></a> Tareas de datos

### <a name="data-bound-controls"></a>Controles enlazados a datos

- [Cómo: rellenar hojas de cálculo con datos de una base de datos](../vsto/how-to-populate-worksheets-with-data-from-a-database.md).

- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Cómo: rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Cómo: rellenar documentos con datos de objetos](../vsto/how-to-populate-documents-with-data-from-objects.md).

- [Cómo: rellenar documentos con datos de una base de datos](../vsto/how-to-populate-documents-with-data-from-a-database.md).

- [Cómo: rellenar documentos con datos de servicios](../vsto/how-to-populate-documents-with-data-from-services.md).

- [Cómo: actualizar un origen de datos con datos de un control host](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

### <a name="cached-data-in-document-level-solutions"></a>Datos almacenados en caché en soluciones de nivel de documento

- [Cómo: almacenar datos en caché para su uso sin conexión o en un servidor](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- [Cómo: almacenar en caché un origen de datos en un documento de Office mediante programación](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).

- [Cómo: almacenar datos en caché en un documento protegido mediante contraseña](../vsto/how-to-cache-data-in-a-password-protected-document.md).

### <a name="custom-xml-data"></a>Datos XML personalizados

- [Cómo: agregar elementos XML personalizados a las personalizaciones de nivel de documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md).

- [Cómo: agregar elementos XML personalizados a documentos mediante complementos de VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md).

## <a name="server-side-document-management-tasks"></a><a name="server"></a> Tareas de administración de documentos de servidor

- [Cómo: quitar extensiones de código administrado de documentos](../vsto/how-to-remove-managed-code-extensions-from-documents.md).

- [Cómo: adjuntar extensiones de código administrado a documentos](../vsto/how-to-attach-managed-code-extensions-to-documents.md).

## <a name="security-tasks"></a><a name="security"></a> Tareas de seguridad

- [Cómo: firmar soluciones de Office](../vsto/how-to-sign-office-solutions.md).

## <a name="deployment-tasks"></a><a name="deployment"></a> Tareas de implementación

- [Cómo: publicar una solución de Office mediante ClickOnce](/previous-versions/bb386095(v=vs.110)).

- [Cómo: publicar una solución de Office de nivel de documento en un servidor de SharePoint mediante ClickOnce](/previous-versions/bb608595(v=vs.110)).

- [Cómo: instalar una solución de Office ClickOnce](/previous-versions/bb608592(v=vs.110)).

- [Cómo: instalar los requisitos previos en equipos de usuarios finales para ejecutar soluciones de Office](/previous-versions/bb608608(v=vs.110)).

- [Cómo: preparar IIS para la implementación de soluciones de Office](/previous-versions/bb608629(v=vs.110)).

- [Cómo: actualizar soluciones de Office implementadas](/previous-versions/bb157871(v=vs.110)).

- [Cómo: cambiar la ruta de instalación de una solución de Office](/previous-versions/bb608626(v=vs.110)).

## <a name="see-also"></a>Vea también
- [Introducción &#40;desarrollo de Office en Visual Studio&#41;](../vsto/getting-started-office-development-in-visual-studio.md)
- [Características disponibles por aplicación y tipo de proyecto de Office](../vsto/features-available-by-office-application-and-project-type.md)
- [Ejemplos y tutoriales de desarrollo de Office](../vsto/office-development-samples-and-walkthroughs.md)