---
title: "Admitir varias vistas del documento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editores [Visual Studio SDK] personalizados - varias vistas de documento"
ms.assetid: c7ec2366-91c4-477f-908d-e89068bdb3e3
caps.latest.revision: 25
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 25
---
# Admitir varias vistas del documento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Puede proporcionar más de una vista de un documento creando datos de documento y los objetos de vista de documentos independientes para el editor.  Algunos casos en los que una vista del documento adicional sería útil son:  
  
-   Compatibilidad con la nueva ventana: Desea que el editor para proporcionar dos o más vistas del mismo tipo, de modo que un usuario que ya tiene una ventana abierta en el editor puede abrir una nueva ventana seleccionando el comando de **Nueva ventana** de menú de **Ventana** .  
  
-   Formulario y compatibilidad con la vista de código: Desea que el editor para proporcionar vistas diferentes tipos.  [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)], por ejemplo, proporciona una vista de formulario y una vista código.  
  
 Para obtener más información sobre esto, vea el procedimiento de CreateEditorInstance en el archivo de EditorFactory.cs en el proyecto de editor personalizado creado por la plantilla de paquete de Visual Studio.  Para obtener más información sobre este proyecto, vea [Tutorial: Crear un Editor personalizado](../extensibility/walkthrough-creating-a-custom-editor.md).  
  
## Sincronizar las vistas  
 Al implementar varias vistas, el objeto del documento es responsable de conservar todas las vistas sincronizado con los datos.  Puede utilizar las interfaces de control de eventos en <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para sincronizar varias vistas con los datos.  
  
 Si no utiliza el objeto de <xref:Microsoft.VisualStudio.TextManager.Interop.VsTextBuffer> para sincronizar varias vistas, debe implementar dispone del sistema de eventos para controlar los cambios realizados en el objeto del documento.  Puede utilizar diferentes niveles de granularidad para mantener varias vistas actualizadas.  Con un valor de la granularidad máxima, como escribe una vista otras vistas se actualizan inmediatamente.  Con granularidad mínima, otras vistas no se actualizan hasta que se provocan.  
  
## Determinar datos de Si es Abrir de Already  
 La tabla en el documento \(RDT\) de la pista \(IDE\) de ayuda del entorno de desarrollo integrado si los datos del documento está abierto, como se muestra en el siguiente diagrama.  
  
 ![Gráfico DocDataView](~/extensibility/media/docdataview.gif "Docdataview")  
Varias vistas  
  
 De forma predeterminada, cada vista \(objeto de vista del documento\) se contiene en su propio marco de ventana \(<xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame>\).  Como se indicó ya, sin embargo, datos de documento puede aparecer en varias vistas.  Para habilitar esto, Visual Studio comprueba el RDT para determinar si el documento en cuestión ya está abierto en un editor.  Si el IDE llama <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory.CreateEditorInstance%2A> para crear el editor, un valor devuelto no NULL en el parámetro de `punkDocDataExisting` indica que el documento está abierto en otro editor.  Para obtener más información sobre cómo funciona el RDT, vea [Tabla de documentos de ejecución](../extensibility/internals/running-document-table.md).  
  
 En la implementación de <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory> , examine el objeto del documento devuelto en `punkDocDataExisting` para determinar si los datos de documento es adecuado para el editor.  \(Por ejemplo, solo los datos HTML deben mostrar por un editor HTML\). Si es necesario, después el generador del editor debe proporcionar una segunda vista para los datos.  Si el parámetro de `punkDocDataExisting` no es `NULL`, es posible cualquiera que el objeto del documento está abierto en otro editor, o, más probable, que los datos del documento está abierto en una vista diferente con el mismo el editor.  Si los datos del documento está abierto en un editor diferente que el generador del editor no admite, Visual Studio no puede abrir el generador del editor.  Para obtener más información, vea [Cómo: adjuntar vistas de datos de documentos](../extensibility/how-to-attach-views-to-document-data.md).