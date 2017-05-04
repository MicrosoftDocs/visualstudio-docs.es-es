---
title: "Accesibilidad en proyectos de Office | Microsoft Docs"
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
  - "accesibilidad [desarrollo de Office en Visual Studio]"
  - "desarrollo de Office en Visual Studio, accesibilidad"
  - "Cinta [desarrollo de Office en Visual Studio], teclas de método abreviado"
  - "teclas de método abreviado [desarrollo de Office en Visual Studio]"
ms.assetid: 48efcf1f-ca49-47ce-99f0-cc99f051aeae
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Accesibilidad en proyectos de Office
  Microsoft Visual Studio y Microsoft Office incluyen muchas características de accesibilidad que permiten compilar soluciones personalizadas que cumplan los requisitos de accesibilidad estándar.  Microsoft publica consejos para la accesibilidad en web.  Para obtener detalles, vea el [sitio web de accesibilidad de Microsoft](http://go.microsoft.com/fwlink/?LinkID=37113).  
  
 En la mayoría de los casos, los proyectos de Office en Visual Studio cumplen las normas de accesibilidad o exponen propiedades que puede establecer para que las soluciones sean accesibles.  Sin embargo, hay algunas características con acceso limitado.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Accesibilidad en tiempo de diseño  
  
### Utilizar teclas de método abreviado en proyectos de nivel de documento  
 Cuando un documento de Microsoft Office Word o un libro de Microsoft Office Excel se abren en Visual Studio, sólo una aplicación recibe a la vez los comandos de tecla de método abreviado.  De forma predeterminada, Visual Studio recibe todos los comandos de teclas de método abreviado, pero se puede hacer que los reciban Word o Excel cuando el documento tenga el foco; para ello, debe seleccionar la opción **Combinación de teclado dinámica** en la página **Configuración de teclado** del cuadro de diálogo **Opciones**.  Para obtener más información, vea [Teclado de Microsoft Office Word, Configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-word-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md) y [Teclado de Microsoft Office Excel, Configuración de teclado de Microsoft Office, cuadro de diálogo Opciones](../vsto/microsoft-office-excel-keyboard-microsoft-office-keyboard-settings-options-dialog-box.md).  
  
### Mostrar teclas de método abreviado para la cinta de opciones en proyectos de nivel de documento  
 Cuando se abre un documento de Word o un libro de Excel en Visual Studio, no puede presionar la tecla Alt para ver las teclas de método abreviado de las pestañas y controles de la cinta de opciones.  Para ver las teclas de método abreviado mientras el documento o el libro están abiertos en el diseñador, lleve a cabo los pasos siguientes.  
  
##### Para ver en el diseñador las teclas de método abreviado correspondientes a los controles y fichas de cinta  
  
1.  En Visual Studio, haga clic en el comando **Opciones** del menú **Herramientas**.  
  
2.  Expanda el nodo **Herramientas de Office** y seleccione **Teclado de Microsoft Office Excel** o **Teclado de Microsoft Office Word**, según corresponda.  
  
3.  Seleccione **Combinación de teclado dinámica**.  
  
     Aparece un mensaje que indica que debe reiniciar Visual Studio para que el cambio surta efecto.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Reinicie Visual Studio y vuelva a abrir el proyecto.  
  
6.  Abra el diseñador del documento o libro del proyecto.  
  
7.  Presione F6 para mostrar las teclas de método abreviado de la cinta de opciones.  
  
## Accesibilidad en tiempo de ejecución  
  
### Controles de formularios Windows Forms en documentos de Office  
 Los controles de formularios Windows Forms exponen las propiedades de accesibilidad para proporcionar información sobre el control a los dispositivos de ayuda de accesibilidad, como los lectores de pantalla.  Puede utilizar estas propiedades de accesibilidad cuando los controles están en un documento de Office en una personalización de nivel de documento.  Para obtener más información, vea [Proporcionar información de accesibilidad de controles en Windows Forms](http://msdn.microsoft.com/library/887dee6f-5059-4d57-957d-7c6fcd4acb10).  
  
 Sin embargo, existen algunas limitaciones de accesibilidad en tiempo de ejecución cuando los controles de formularios Windows Forms están hospedados en un libro de Excel o en un documento de Word:  
  
-   No puede desplazarse de uno control a otro usando la tecla Tab.  
  
-   Los controles de un documento se deshabilitan cuando se cambia la configuración de zoom del documento a un valor distinto del 100%.  
  
 Para obtener información sobre las limitaciones de los controles de Windows Forms en los documentos, vea [Limitaciones de los controles de formularios Windows Forms en los documentos de Office](../vsto/limitations-of-windows-forms-controls-on-office-documents.md).  
  
### Paneles de acciones y paneles de tareas personalizados  
 Cuando un panel de acciones o un panel de tareas personalizado tienen el foco, se obtiene acceso a los controles de la misma forma que lo haría con los controles de una aplicación de formularios Windows Forms.  Para mover el cursor entre el panel de acciones y el documento, puede presionar **F6**.  
  
 Para obtener más información acerca de los paneles de acciones y los paneles de tareas personalizados, vea [Información general sobre paneles de acciones](../vsto/actions-pane-overview.md) y [Paneles de tareas personalizados](../vsto/custom-task-panes.md).  
  
### Modos de presentación  
 Visual Studio presenta las limitaciones siguientes relacionadas con los modos de presentación:  
  
-   Los controles de un documento de Word o de una hoja de cálculo de Excel se deshabilitan cuando se cambia la configuración de zoom del documento a un valor distinto de 100%.  
  
-   El cuadro de diálogo **Nuevo proyecto** no muestra los controles correctamente si un usuario cambia las opciones de accesibilidad del equipo a **Utilizar contraste alto**.  
  
 Puede utilizar Aumentar para superar estas limitaciones.  El ampliador es una utilidad de presentación de Microsoft Windows que crea una ventana independiente donde se muestra una parte ampliada de la pantalla.  
  
## Vea también  
 [Desarrollar soluciones de Office](../vsto/developing-office-solutions.md)   
 [Controles en documentos de Office](../vsto/controls-on-office-documents.md)   
 [Accesibilidad para personas con discapacidades](../ide/reference/accessibility-for-people-with-disabilities.md)   
 [Características de accesibilidad de Visual Studio](../ide/reference/accessibility-features-of-visual-studio.md)  
  
  