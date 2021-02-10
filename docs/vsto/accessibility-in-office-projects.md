---
title: Accesibilidad en proyectos de Office
description: Aprenda cómo Microsoft Office proyectos incluyen muchas características de accesibilidad que le permiten crear soluciones personalizadas que cumplan los requisitos de accesibilidad estándar.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 4021517aa296f3c1e6355b82260b00590181f4cb
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99955156"
---
# <a name="accessibility-in-office-projects"></a>Accesibilidad en proyectos de Office

Microsoft Visual Studio e Microsoft Office incluyen muchas características de accesibilidad que permiten crear soluciones personalizadas que cumplan los requisitos de accesibilidad estándar. Microsoft publica instrucciones para la accesibilidad en la Web. Para obtener más información, consulte el [sitio web de accesibilidad](https://www.microsoft.com/accessibility/).

En la mayoría de los casos, los proyectos de Office en Visual Studio cumplen con los estándares de accesibilidad o expone propiedades que se pueden establecer para que las soluciones sean accesibles. Sin embargo, hay algunas características que tienen una accesibilidad limitada.

[!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

## <a name="accessibility-at-design-time"></a>Accesibilidad en tiempo de diseño

### <a name="use-shortcut-keys-in-document-level-projects"></a>Usar las teclas de método abreviado en los proyectos de nivel de documento
 Cuando un documento de Microsoft Office Word o un libro de Excel Microsoft Office está abierto en Visual Studio, solo una aplicación a la vez recibe los comandos de tecla de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Word o Excel los reciban cuando el documento tenga el foco seleccionando **esquema de teclado dinámico** en la página **configuración del teclado** del cuadro de diálogo **Opciones** . Para obtener más información, vea [Microsoft Office teclado de Word, Microsoft Office configuración del teclado, opciones (cuadro de diálogo](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) ) y [Microsoft Office teclado de Excel, Microsoft Office configuración del teclado, opciones (cuadro de diálogo](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md)).

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Mostrar teclas de método abreviado para la cinta de opciones en proyectos de nivel de documento
 Cuando un documento de Word o un libro de Excel está abierto en Visual Studio, no puede presionar la tecla **Alt** para ver las teclas de método abreviado de las pestañas y los controles de la cinta de opciones. Para ver las teclas de método abreviado mientras el documento o libro está abierto en el diseñador, realice los pasos siguientes.

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Para ver las teclas de método abreviado para las pestañas y controles de la cinta de opciones en el diseñador

1. En Visual Studio, en el menú **herramientas** , haga clic en **Opciones**.

2. Expanda el nodo **herramientas de Office** y seleccione **Microsoft Office teclado de Excel** o **Microsoft Office teclado de Word**, según corresponda.

3. Seleccione **esquema de teclado dinámico**.

     Aparece un mensaje que indica que debe reiniciar Visual Studio para que el cambio surta efecto.

4. Haga clic en **OK**.

5. Reinicie Visual Studio y vuelva a abrir el proyecto.

6. Abra el diseñador de documentos o libros del proyecto.

7. Presione **F6** para mostrar las teclas de método abreviado de la cinta.

## <a name="accessibility-at-run-time"></a>Accesibilidad en tiempo de ejecución

### <a name="windows-forms-controls-on-office-documents"></a>Windows Forms controles en documentos de Office
 Windows Forms controles exponen propiedades de accesibilidad para proporcionar información sobre el control a las ayudas de accesibilidad, como lectores de pantalla. Puede aprovechar estas propiedades de accesibilidad cuando los controles se encuentran en un documento de Office en una personalización de nivel de documento. Para obtener más información, vea [proporcionar información de accesibilidad para los controles de Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).

 Sin embargo, hay algunas limitaciones de accesibilidad en tiempo de ejecución cuando Windows Forms controles se hospedan en un libro de Excel o en un documento de Word:

- No se puede tabular de un control a otro.

- Los controles de un documento se deshabilitan cuando se cambia la configuración de zoom del documento a un valor distinto del 100%.

  Para obtener información sobre las limitaciones de los controles de Windows Forms en documentos, vea [limitaciones de los controles de Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).

### <a name="actions-panes-and-custom-task-panes"></a>Paneles de acciones y paneles de tareas personalizados
 Cuando un panel de acciones o un panel de tareas personalizado tiene el foco, tiene acceso a los controles de la misma forma que lo haría con los controles de una aplicación Windows Forms. Para desplazar el cursor entre el panel de acciones y el documento, puede presionar **F6**.

 Para obtener más información sobre los paneles de acciones y los paneles de tareas personalizados, vea [información general del panel de acciones](../vsto/actions-pane-overview.md) y [paneles de tareas personalizados](../vsto/custom-task-panes.md).

### <a name="display-modes"></a>Modos de pantalla

Visual Studio tiene las siguientes limitaciones relacionadas con los modos de presentación:

- Los controles de un documento de Word o de una hoja de cálculo de Excel se deshabilitan cuando se cambia la configuración de zoom del documento a un valor distinto del 100%.

- El cuadro de diálogo **nuevo proyecto** no muestra los controles correctamente si un usuario cambia las opciones de accesibilidad del equipo para **utilizar contraste alto**.

Puede usar el ampliador para superar estas limitaciones. La lupa es una utilidad de visualización de Windows que crea una ventana independiente que muestra una parte ampliada de la pantalla.

## <a name="see-also"></a>Vea también

- [Desarrollo de soluciones de Office](../vsto/developing-office-solutions.md)
- [Controles en documentos de Office](../vsto/controls-on-office-documents.md)
- [Accesibilidad para personas con discapacidades](../ide/reference/accessibility-features-of-visual-studio.md)
- [Características de accesibilidad de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)