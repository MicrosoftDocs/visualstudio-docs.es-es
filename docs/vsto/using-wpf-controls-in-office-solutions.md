---
title: Utilizar controles WPF en soluciones de Office | Documentos de Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords: WPF [Office development in Visual Studio]
ms.assetid: 305a212b-0a95-40ad-87aa-22896fe80a04
caps.latest.revision: "25"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: office
ms.openlocfilehash: 9cbb87017b910accae5ebc63b648691c50f88476
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="using-wpf-controls-in-office-solutions"></a>Usar controles de WPF en soluciones de Office
  Aunque las soluciones creadas con las herramientas de desarrollo de Visual Studio para Office están diseñadas para funcionar directamente con controles de Windows Forms, también puede usar controles WPF en sus soluciones. Windows Presentation Foundation (WPF) es una alternativa a los formularios Windows Forms para diseñar interfaces de usuario. WPF utiliza un lenguaje de marcado denominado lenguaje XAML que proporciona nuevas técnicas con el fin de incorporar interfaces de usuario, multimedia y documentos. Para obtener más información, consulte [Introducción a WPF en Visual Studio 2015](/dotnet/framework/wpf/getting-started/introduction-to-wpf-in-vs).  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 Cualquier elemento de la interfaz de usuario que pueda hospedar controles de Windows Forms en una solución de Office también puede hospedar controles WPF. Entre estos elementos se incluyen los siguientes:  
  
-   Documentos y hojas de cálculo en personalizaciones de nivel de documento.  
  
-   Paneles de acciones en personalizaciones de nivel de documento.  
  
-   Paneles de tareas personalizados en complementos de VSTO.  
  
-   Áreas de formulario en complementos de VSTO para Outlook.  
  
## <a name="adding-wpf-controls-to-office-projects-at-design-time"></a>Agregar controles WPF a proyectos de Office en tiempo de diseño  
 No puede agregar controles WPF directamente a los elementos de la interfaz de usuario en las soluciones de Office. En su lugar, agregue un **Control de usuario (WPF)** elemento al proyecto y usarlo como la superficie de diseño para los controles WPF. A continuación, agregue el control de usuario de WPF a un elemento de la interfaz de usuario del proyecto.  
  
#### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Para agregar controles de WPF a un panel de acciones, panel de tareas personalizado o área de formulario  
  
1.  Abra un proyecto al que desea agregar un panel de tareas personalizado, un panel de acciones o un área de formulario.  
  
2.  Agregar un **Control de usuario (WPF)** elemento al proyecto.  
  
3.  Desde el **cuadro de herramientas**, agregar controles WPF a la superficie de diseño del control de usuario WPF.  
  
     De forma predeterminada, cuando el Diseñador de controles de usuario WPF está abierto, el **cuadro de herramientas** contiene solo los controles WPF.  
  
4.  Compile el proyecto.  
  
5.  Agregue un panel de acciones, área de formulario o panel de tareas personalizado al proyecto:  
  
    -   Para las áreas de formulario, agregue un **área de formulario de Outlook** elemento al proyecto. Para obtener más información, consulte [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).  
  
    -   Para los paneles de acciones, agregue un **Control del panel de acciones** o **Control de usuario** elemento al proyecto. Para obtener más información, consulte [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md) y [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).  
  
    -   Para los paneles de tareas personalizados, agregue un **Control de usuario** elemento al proyecto. Para obtener más información, consulte [Cómo: agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).  
  
6.  Desde el *ProjectName* **controles de usuario de WPF** pestaña de la **cuadro de herramientas**, arrastre el control de usuario WPF hasta el diseñador para el panel de acciones, área de formulario o panel de tareas personalizado.  
  
     Visual Studio crea automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost> que hospeda el control de usuario de WPF en el elemento de la interfaz de usuario.  
  
7.  Recompile el proyecto.  
  
#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Para agregar controles de WPF a un documento u hoja de cálculo en un proyecto de nivel de documento  
  
1.  Abra un proyecto de nivel de documento para Word o Excel.  
  
2.  Agregar un **Control de usuario (WPF)** elemento al proyecto.  
  
3.  Desde el **cuadro de herramientas**, agregar controles WPF a la superficie de diseño del control de usuario WPF.  
  
4.  Compile el proyecto.  
  
5.  Agregar un **Control de usuario** elemento (es decir, un control de usuario de formularios Windows Forms) al proyecto.  
  
6.  Abra el diseñador para el control de usuario de formularios Windows Forms.  
  
7.  Desde el *ProjectName* **controles de usuario de WPF** pestaña de la **cuadro de herramientas**, arrastre el control de usuario WPF hasta el diseñador.  
  
     Visual Studio crea automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost> que hospeda el control de usuario de WPF en el control de usuario de formularios Windows Forms.  
  
8.  Escriba código que agregue mediante programación el control de usuario de formularios Windows Forms al documento o libro. Para obtener más información, consulta [Adding Controls to Office Documents at Run Time](../vsto/adding-controls-to-office-documents-at-run-time.md).  
  
    > [!NOTE]  
    >  No puede arrastrar el control de usuario de formularios Windows Forms hacia el documento o la hoja de cálculo en el diseñador.  
  
9. Recompile el proyecto.  
  
## <a name="hosting-wpf-controls-by-using-the-elementhost-class"></a>Hospedar controles de WPF mediante la clase ElementHost  
 Visual Studio proporciona características que le ayudan a usar controles de Windows Forms en las soluciones de Office, pero no proporciona características similares para los controles WPF. Por ejemplo, puede agregar los controles de formularios Windows Forms a documentos y hojas de cálculo en tiempo de diseño, arrastre controles desde el **cuadro de herramientas**, o en tiempo de ejecución mediante el uso de métodos auxiliares. Sin embargo, estas herramientas no están disponibles para los controles de WPF.  
  
 Los controles de WPF utilizan la clase <xref:System.Windows.Forms.Integration.ElementHost> como una capa de la integración entre un control de formularios Windows Forms y los controles de WPF. Al agregar controles de WPF a la solución en tiempo de diseño, Visual Studio genera automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost>.  
  
## <a name="wpf-resources"></a>Recursos de WPF  
 Para obtener más información sobre los problemas de arquitectura y diseño relacionados con el hospedaje de controles de WPF en controles de formularios y formularios Windows Forms, vea los temas siguientes:  
  
-   [Arquitectura de entrada de interoperabilidad entre formularios Windows Forms y WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)  
  
-   [Asignación de propiedades en formularios Windows Forms y WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)  
  
-   [Interoperabilidad entre Windows Forms y WPF](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)  
  
-   [Controles de Windows Forms y controles equivalentes de WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)  
  
 Para obtener más información sobre cómo agregar controles de WPF a los controles de formularios y formularios Windows Forms en Visual Studio en tiempo de diseño, vea los temas siguientes:  
  
-   [Tutorial: Crear nuevo contenido de WPF en Windows Forms en tiempo de diseño](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)  
  
-   [Tutorial: Organizar el contenido de WPF en Windows Forms en tiempo de diseño](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)  
  
-   [Tutorial: Aplicar estilos al contenido de WPF](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)  
  
## <a name="see-also"></a>Vea también  
 [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)   
 [Controles en documentos de Office información general sobre formularios Windows Forms](../vsto/windows-forms-controls-on-office-documents-overview.md)   
 [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md)   
 [Paneles de tareas personalizados](../vsto/custom-task-panes.md)   
 [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)   
 [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)   
 [Cómo: agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)   
 [Cómo: Agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)  
  
  