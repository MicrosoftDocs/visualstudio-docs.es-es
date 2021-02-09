---
title: Usar controles de WPF en soluciones de Office
description: Obtenga información sobre cómo puede usar controles de Windows Presentation Foundation (WPF) para diseñar interfaces de usuario en Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- WPF [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 7bc720e6218e4cbb76b14f356d190b738e31ede3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99921904"
---
# <a name="use-wpf-controls-in-office-solutions"></a>Usar controles de WPF en soluciones de Office

Aunque las soluciones creadas con las herramientas de desarrollo de Visual Studio para Office están diseñadas para funcionar directamente con controles de Windows Forms, también puede usar controles WPF en sus soluciones. Windows Presentation Foundation (WPF) es una alternativa a los formularios Windows Forms para diseñar interfaces de usuario. WPF utiliza un lenguaje de marcado denominado lenguaje XAML que proporciona nuevas técnicas con el fin de incorporar interfaces de usuario, multimedia y documentos. Para obtener más información, vea [información general sobre WPF](/dotnet/framework/wpf/introduction-to-wpf).

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

Cualquier elemento de la interfaz de usuario que pueda hospedar controles de Windows Forms en una solución de Office también puede hospedar controles WPF. Entre estos elementos se incluyen los siguientes:

- Documentos y hojas de cálculo en personalizaciones de nivel de documento.

- Paneles de acciones en personalizaciones de nivel de documento.

- Paneles de tareas personalizados en complementos de VSTO.

- Áreas de formulario en complementos de VSTO para Outlook.

## <a name="add-wpf-controls-to-office-projects-at-design-time"></a>Agregar controles de WPF a proyectos de Office en tiempo de diseño

No puede agregar controles WPF directamente a los elementos de la interfaz de usuario en las soluciones de Office. En su lugar, agregue un elemento **control de usuario (WPF)** al proyecto y úselo como superficie de diseño para los controles de WPF. A continuación, agregue el control de usuario de WPF a un elemento de la interfaz de usuario del proyecto.

### <a name="to-add-wpf-controls-to-an-actions-pane-custom-task-pane-or-form-region"></a>Para agregar controles de WPF a un panel de acciones, panel de tareas personalizado o área de formulario

1. Abra un proyecto al que desea agregar un panel de tareas personalizado, un panel de acciones o un área de formulario.

2. Agregue un elemento **control de usuario (WPF)** al proyecto.

3. En el **cuadro de herramientas**, agregue controles de WPF a la superficie de diseño del control de usuario de WPF.

     De forma predeterminada, cuando el diseñador de controles de usuario de WPF está abierto, el **cuadro de herramientas** solo contiene controles WPF.

4. Compile el proyecto.

5. Agregue un panel de acciones, área de formulario o panel de tareas personalizado al proyecto:

    - En el caso de las áreas de formulario, agregue un elemento **área de formulario de Outlook** al proyecto. Para obtener más información, vea [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md).

    - Para los paneles de acciones, agregue un **control del panel de acciones** o un elemento de control de **usuario** al proyecto. Para obtener más información, vea [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md).

    - En el caso de los paneles de tareas personalizados, agregue un elemento **control de usuario** al proyecto. Para obtener más información, consulte [Cómo: agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md).

6. En la pestaña *nombreDeProyecto* **controles de usuario de WPF** del cuadro de **herramientas**, arrastre el control de usuario de WPF hasta el diseñador para el panel de acciones, área de formulario o panel de tareas personalizado.

     Visual Studio crea automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost> que hospeda el control de usuario de WPF en el elemento de la interfaz de usuario.

7. Recompile el proyecto.

#### <a name="to-add-wpf-controls-to-a-document-or-worksheet-in-a-document-level-project"></a>Para agregar controles de WPF a un documento u hoja de cálculo en un proyecto de nivel de documento

1. Abra un proyecto de nivel de documento para Word o Excel.

2. Agregue un elemento **control de usuario (WPF)** al proyecto.

3. En el **cuadro de herramientas**, agregue controles de WPF a la superficie de diseño del control de usuario de WPF.

4. Compile el proyecto.

5. Agregue un elemento de **control de usuario** (es decir, un control de usuario Windows Forms) al proyecto.

6. Abra el diseñador para el control de usuario de formularios Windows Forms.

7. En la pestaña *nombreDeProyecto* **controles de usuario de WPF** del cuadro de **herramientas**, arrastre el control de usuario de WPF hasta el diseñador.

     Visual Studio crea automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost> que hospeda el control de usuario de WPF en el control de usuario de formularios Windows Forms.

8. Escriba código que agregue mediante programación el control de usuario de formularios Windows Forms al documento o libro. Para obtener más información, vea [Agregar controles a documentos de Office en tiempo de ejecución](../vsto/adding-controls-to-office-documents-at-run-time.md).

    > [!NOTE]
    > No puede arrastrar el control de usuario de formularios Windows Forms hacia el documento o la hoja de cálculo en el diseñador.

9. Recompile el proyecto.

## <a name="host-wpf-controls-by-using-the-elementhost-class"></a>Hospedar controles de WPF mediante la clase ElementHost

Visual Studio proporciona características que le ayudan a usar controles de Windows Forms en las soluciones de Office, pero no proporciona características similares para los controles WPF. Por ejemplo, puede Agregar controles Windows Forms a documentos y hojas de cálculo en tiempo de diseño arrastrando los controles del **cuadro de herramientas** o en tiempo de ejecución mediante métodos auxiliares. Sin embargo, estas herramientas no están disponibles para los controles de WPF.

Los controles de WPF utilizan la clase <xref:System.Windows.Forms.Integration.ElementHost> como una capa de la integración entre un control de formularios Windows Forms y los controles de WPF. Al agregar controles de WPF a la solución en tiempo de diseño, Visual Studio genera automáticamente un objeto <xref:System.Windows.Forms.Integration.ElementHost>.

## <a name="wpf-resources"></a>Recursos de WPF

Para obtener más información sobre los problemas de arquitectura y diseño relacionados con el hospedaje de controles de WPF en controles de formularios y formularios Windows Forms, vea los temas siguientes:

- [Arquitectura de entrada de interoperabilidad de Windows Forms y WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-interoperability-input-architecture)

- [Asignación de propiedades de Windows Forms y WPF](/dotnet/framework/wpf/advanced/windows-forms-and-wpf-property-mapping)

- [Interoperabilidad de WPF y Windows Forms](/dotnet/framework/wpf/advanced/wpf-and-windows-forms-interoperation)

- [Controles de Windows Forms y controles equivalentes de WPF](/dotnet/framework/wpf/advanced/windows-forms-controls-and-equivalent-wpf-controls)

Para obtener más información sobre cómo agregar controles de WPF a los controles de formularios y formularios Windows Forms en Visual Studio en tiempo de diseño, vea los temas siguientes:

- [Tutorial: crear nuevo contenido de WPF en Windows Forms en tiempo de diseño](/dotnet/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time)

- [Tutorial: organizar el contenido de WPF en Windows Forms en tiempo de diseño](/dotnet/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time)

- [Tutorial: contenido de WPF de estilo](/dotnet/framework/winforms/advanced/walkthrough-styling-wpf-content)

## <a name="see-also"></a>Vea también

- [Personalización de la interfaz de usuario de Office](../vsto/office-ui-customization.md)
- [Información general sobre los controles de Windows Forms en documentos de Office](../vsto/windows-forms-controls-on-office-documents-overview.md)
- [Información general del panel de acciones](../vsto/actions-pane-overview.md)
- [Paneles de tareas personalizados](../vsto/custom-task-panes.md)
- [Crear áreas de formulario de Outlook](../vsto/creating-outlook-form-regions.md)
- [Cómo: agregar un panel de acciones a documentos de Word o libros de Excel](../vsto/how-to-add-an-actions-pane-to-word-documents-or-excel-workbooks.md)
- [Cómo: agregar un panel de tareas personalizado a una aplicación](../vsto/how-to-add-a-custom-task-pane-to-an-application.md)
- [Cómo: agregar un área de formulario a un proyecto de complemento de Outlook](../vsto/how-to-add-a-form-region-to-an-outlook-add-in-project.md)
