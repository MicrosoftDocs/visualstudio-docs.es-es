---
title: Accesibilidad en proyectos de Office
ms.custom: ''
ms.date: 02/02/2017
ms.technology: office-development
ms.prod: visual-studio-dev15
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office development in Visual Studio, accessibility
- shortcut keys [Office development in Visual Studio]
- Ribbon [Office development in Visual Studio], shortcut keys
- accessibility [Office development in Visual Studio]
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e7d056d8f5cb014d48827faf0ec10a8a23bd8d03
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49938830"
---
# <a name="accessibility-in-office-projects"></a>Accesibilidad en proyectos de Office
  Microsoft Visual Studio y Microsoft Office incluyen muchas características de accesibilidad que permiten crear soluciones personalizadas que satisfagan los requisitos de accesibilidad estándar. Microsoft publica directrices para mejorar la accesibilidad en la Web. Para obtener más información, consulte el [sitio Web de accesibilidad](http://go.microsoft.com/fwlink/?LinkID=37113).  

 En la mayoría de los casos, los proyectos de Office en Visual Studio cumplen accesibilidad estándares o expone propiedades que se pueden establecer para que sea accesible sus soluciones. Sin embargo, hay algunas características con acceso limitado.  

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  

## <a name="accessibility-at-design-time"></a>Accesibilidad en tiempo de diseño  

### <a name="use-shortcut-keys-in-document-level-projects"></a>Usar teclas de método abreviado en proyectos de nivel de documento  
 Cuando un documento de Microsoft Office Word o un libro de Microsoft Office Excel está abierto en Visual Studio, sólo una aplicación a la vez recibe los comandos de teclas de método abreviado. De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero puede hacer que Word o Excel recibirlos cuando el documento tiene el foco seleccionando **combinación de teclado dinámico** en el **configuración del teclado** página de la **opciones** cuadro de diálogo. Para obtener más información, consulte [teclado de Microsoft Office Word, configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) y [teclado de Microsoft Office Excel, configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  

### <a name="display-shortcut-keys-for-the-ribbon-in-document-level-projects"></a>Mostrar teclas de método abreviado de la cinta de opciones en los proyectos de nivel de documento  
 Cuando un documento de Word o un libro de Excel se abre en Visual Studio, no se puede presionar la **Alt** tecla para ver las teclas de método abreviado para las fichas y controles en la cinta de opciones. Para ver las teclas de método abreviado mientras está abierto en el diseñador del documento o libro, realice los pasos siguientes.  

#### <a name="to-view-shortcut-keys-for-ribbon-tabs-and-controls-in-the-designer"></a>Para ver las teclas de método abreviado para las fichas y controles Ribbon en el diseñador  

1.  En Visual Studio, en el **herramientas** menú, haga clic en **opciones**.  

2.  Expanda el **Office Tools** nodo y seleccione **teclado de Microsoft Office Excel** o **teclado de Microsoft Office Word**, según corresponda.  

3.  Seleccione **combinación de teclado dinámico**.  

     Aparece un mensaje que indica que debe reiniciar Visual Studio para que el cambio surta efecto.  

4.  Haga clic en **Aceptar**.  

5.  Reinicie Visual Studio y vuelva a abrir el proyecto.  

6.  Abra el diseñador para el proyecto de documento o libro.  

7.  Presione **F6** para mostrar las teclas de método abreviado de la cinta de opciones.  

## <a name="accessibility-at-runtime"></a>Accesibilidad en tiempo de ejecución  

### <a name="windows-forms-controls-on-office-documents"></a>Controles de Windows Forms en documentos de Office  
 Controles de formularios Windows Forms exponen las propiedades de accesibilidad para proporcionar información sobre el control a las ayudas de accesibilidad, como lectores de pantalla. Puede aprovechar estas propiedades de accesibilidad cuando los controles están en un documento de Office en una personalización de nivel de documento. Para obtener más información, consulte [proporcionar información de accesibilidad de controles de Windows Forms](/dotnet/framework/winforms/controls/providing-accessibility-information-for-controls-on-a-windows-form).  

 Sin embargo, existen algunas limitaciones de accesibilidad en tiempo de ejecución cuando se hospedan controles de formularios Windows Forms en un libro de Excel o un documento de Word:  

- No se puede pestaña de un control a otro.  

- Se deshabilitan los controles en un documento al cambiar la configuración del zoom del documento a cualquier cosa que no sea 100%.  

  Para obtener información acerca de las limitaciones de los controles de Windows Forms en documentos, consulte [controla las limitaciones de los formularios Windows Forms en documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  

### <a name="actions-panes-and-custom-task-panes"></a>Paneles de acciones y paneles de tareas personalizados  
 Cuando un panel de acciones o el panel de tareas personalizado tiene el foco, obtener acceso a los controles de la misma manera que para acceder a los controles en una aplicación de Windows Forms. Para mover el cursor entre el panel de acciones y el documento, puede presionar **F6**.  

 Para obtener más información acerca de los paneles de acciones y paneles de tareas personalizados, vea [información general sobre el panel de acciones](../vsto/actions-pane-overview.md) y [paneles de tareas personalizados](../vsto/custom-task-panes.md).  

### <a name="display-modes"></a>Modos de presentación  
 Visual Studio tiene las siguientes limitaciones relacionadas con los modos de presentación:  

- Controles en un documento de Word o una hoja de cálculo de Excel se deshabilitan cuando se cambia la configuración del zoom del documento a cualquier cosa que no sea 100%.  

- El **nuevo proyecto** cuadro de diálogo no muestra los controles correctamente si un usuario cambia las opciones de accesibilidad del equipo a **Usar contraste alto**.  

  Puede usar el Ampliador para superar estas limitaciones. El Ampliador es una utilidad de presentación de Windows que crea una ventana independiente que muestra una parte ampliada de la pantalla.  

## <a name="see-also"></a>Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Accesibilidad para personas con discapacidades](/visualstudio/ide/reference/accessibility-for-people-with-disabilities)   
 [Características de accesibilidad de Visual Studio](/visualstudio/ide/reference/accessibility-features-of-visual-studio)  
