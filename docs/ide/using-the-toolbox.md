---
title: Usar el Cuadro de herramientas | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.chooseitems
- vs.toolboxpages.activexcontrols
- VS.CHOOSEITEMS.windowsuixamlcomponents
- VS.chooseitems.silverlightcomponents
- VC.EDITORS.RIBBON
- vs.customizetoolbox
- VS.chooseitems.System.Workflow_Components
- vs.chooseitems.frameworkcomponents
- VS.ToolboxPages..NET_Framework_Components
- VS.chooseitems.Microsoft.VisualStudio.Toolbox.VsToolboxPage
- vs.chooseitems.comcomponents
- vs.toolboxpages.NGWS_components
helpviewer_keywords:
- toolbox, adding items
- Visual Studio, toolbox
- toolbox, tabs
- toolbox
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: c41a77a1fdb36ab8610ebc648cacb1568b330de8
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-toolbox"></a>Usar el Cuadro de herramientas

Puede usar el cuadro de herramientas para agregar controles y otros elementos al proyecto. Puede arrastrar y colocar distintos controles en la superficie del diseñador que use y cambiar su tamaño y posición.

El cuadro de herramientas aparece junto con las vistas de diseñador, como la vista de diseñador de un archivo XAML. En el cuadro de herramientas solo se muestran los controles que se pueden usar en el diseñador actual.

La versión de .NET Framework del proyecto también afecta al conjunto de controles visibles en el cuadro de herramientas. Para establecer que el proyecto use otra versión de .NET Framework, seleccione el nodo del proyecto en el **Explorador de soluciones** y, después, vaya a **Propiedades/Aplicación/Plataforma de destino**.

## <a name="managing-the-toolbox-and-its-controls"></a>Administrar el cuadro de herramientas y sus controles

De manera predeterminada, el cuadro de herramientas está contraído en la izquierda del IDE de Visual Studio y aparece cuando se desplaza el cursor por encima. Puede anclar el cuadro de herramientas (haciendo clic en el icono **Anclar** de la barra de herramientas del cuadro de herramientas), de manera que permanezca abierto al mover el cursor. También puede desacoplar la ventana del cuadro de herramientas y arrastrarla a cualquier punto de la pantalla. Puede acoplar, desacoplar y ocultar el cuadro de herramientas si hace clic con el botón derecho en su barra de herramientas y selecciona una de las opciones.

Puede reorganizar los elementos de una pestaña del cuadro de herramientas o agregar pestañas y elementos personalizados por medio de los siguientes comandos del menú contextual:

-   **Cambiar nombre de elemento**: permite cambiar el nombre del elemento seleccionado.  
  
-   **Mostrar todo**: muestra todos los controles posibles (no solo los correspondientes al diseñador actual).  
  
-   **Vista de lista**: muestra los controles en una lista vertical. Si se deja sin marcar, los controles aparecen horizontalmente.  
  
-   **Elegir elementos**: abre el cuadro de diálogo **Elegir elementos del cuadro de herramientas** para que pueda especificar los elementos que aparecen en el **Cuadro de herramientas**. Para mostrar u ocultar un elemento, active o desactive su casilla.  
  
-   **Ordenar elementos alfabéticamente**: ordena los elementos por el nombre.  
  
-   **Restablecer barra de herramientas**: restaura la configuración y los elementos predeterminados del cuadro de herramientas.  
  
-   **Agregar pestaña**: agrega una nueva pestaña del cuadro de herramientas.  
  
-   **Subir**: mueve el elemento seleccionado hacia arriba.  
  
-   **Bajar**: mueve el elemento seleccionado hacia abajo.  

## <a name="creating-and-distributing-custom-toolbox-controls"></a>Crear y distribuir controles personalizados del cuadro de herramientas

Puede crear un control personalizado del cuadro de herramientas en Visual Basic o Visual C#, y puede partir de una plantilla de proyecto basada en [Windows Presentation Foundation](../extensibility/creating-a-wpf-toolbox-control.md) o [Windows Forms](../extensibility/creating-a-windows-forms-toolbox-control.md). Después, puede distribuir el control a sus compañeros de equipo o publicarlo en la web con el [Instalador de controles del cuadro de herramientas](http://download.microsoft.com/download/8/3/6/836657BD-9CCB-4ED4-B9D2-FB769473B284/TCI_whitepaper.docx).

## <a name="see-also"></a>Vea también

[Escribir código en el editor](../ide/writing-code-in-the-code-and-text-editor.md)