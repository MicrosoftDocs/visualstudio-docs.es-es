---
title: Opciones (Cuadro de diálogo) (Visual Studio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: df56cdef77c8f189a27d52ea624359bb8dfe3bca
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="options-dialog-box-visual-studio"></a>Opciones (Cuadro de diálogo) (Visual Studio)
El cuadro de diálogo **Opciones** le permite configurar el entorno de desarrollo integrado (IDE) según sus necesidades. Por ejemplo, puede establecer una ubicación de almacenamiento predeterminada para sus proyectos, cambiar la apariencia predeterminada y el comportamiento de las ventanas y crear accesos directos para los comandos más usados. Existen también opciones específicas a su lenguaje de desarrollo y plataforma. Puede tener acceso a **Opciones** en el menú **Herramientas**.  
  
> [!NOTE]
>  Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../../ide/personalizing-the-visual-studio-ide.md).  
  
## <a name="layout-of-the-options-dialog-box"></a>Diseño del cuadro de diálogo Opciones  
 El cuadro de diálogo **Opciones** está dividido en dos partes: un panel de navegación a la izquierda y un área de visualización a la derecha. El control de árbol en el panel de navegación incluye nodos de carpeta, como Entorno, Editor de texto, Proyectos y soluciones y Control de código fuente. Expanda cualquier nodo de carpeta para mostrar las páginas de opciones que contiene. Cuando seleccione el nodo de una página determinada, sus opciones aparecen en el área de visualización.  
  
 Las opciones de una característica del IDE no aparecen en el panel de navegación hasta que la característica se carga en la memoria. Por lo tanto, las mismas opciones pueden no mostrarse cuando empieza una sesión que se han mostrado cuando ha finalizado la última. Cuando crea un proyecto o ejecuta un comando que usa una aplicación determinada, los nodos de las opciones relevantes se agregan al cuadro de diálogo Opciones. Estas opciones agregadas seguirán estando disponibles mientras que la característica del IDE siga estando en la memoria.  
  
> [!NOTE]
>  Algunas colecciones de configuraciones definen el número de páginas que aparecen en el panel de navegación del cuadro de diálogo Opciones. Puede elegir ver todas las páginas posibles seleccionando **Mostrar todas las configuraciones**.  
  
## <a name="how-options-are-applied"></a>Cómo se aplican las opciones  
 Al hacer clic en Aceptar en el cuadro de diálogo **Opciones** se guardan todas las opciones en todas las páginas. Al hacer clic en Cancelar en cualquier página se cancelan todas las solicitudes de cambio, incluidas las que se acaban de realizar en otras páginas de **opciones**. Algunos cambios en la configuración de opciones, como los que se realizan en el [cuadro de diálogo Fuentes y colores, Entorno, Opciones](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md) solo surtirán efecto después de que cierre y vuelva a abrir Visual Studio.  
  
### <a name="show-all-settings"></a>Mostrar todas las configuraciones  
 Al seleccionar o anular la selección de **Mostrar todas las configuraciones** se aplican todos los cambios que ha realizado en el cuadro de diálogo **Opciones**, incluso cuando todavía no ha hecho clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Personalizar el editor](../../ide/customizing-the-editor.md)