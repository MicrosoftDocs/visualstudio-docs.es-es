---
title: Opciones (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages
helpviewer_keywords:
- Tools Options settings
- Options dialog box
- Options dialog box, development environment
- tools [Visual Studio], customizing
ms.assetid: 02b09877-1df1-4531-a0d1-a4ca17c7f857
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: bc659641e64bde9da4f1e05abf285fbdec1877e3
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MTE95
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65674842"
---
# <a name="options-dialog-box-visual-studio"></a>Opciones (Cuadro de diálogo) (Visual Studio)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

El cuadro de diálogo **Opciones** le permite configurar el entorno de desarrollo integrado (IDE) según sus necesidades. Por ejemplo, puede establecer una ubicación de almacenamiento predeterminada para sus proyectos, cambiar la apariencia predeterminada y el comportamiento de las ventanas y crear accesos directos para los comandos más usados. Existen también opciones específicas a su lenguaje de desarrollo y plataforma. Puede tener acceso a **Opciones** en el menú **Herramientas**.

> [!NOTE]
> Las opciones disponibles en los cuadros de diálogo, así como los nombres y las ubicaciones de los comandos de menú que se ven, podrían diferir de lo que se describe en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="layout-of-the-options-dialog-box"></a>Diseño del cuadro de diálogo Opciones
 El cuadro de diálogo **Opciones** está dividido en dos partes: un panel de navegación a la izquierda y un área de visualización a la derecha. El control de árbol en el panel de navegación incluye nodos de carpeta, como Entorno, Editor de texto, Proyectos y soluciones y Control de código fuente. Expanda cualquier nodo de carpeta para mostrar las páginas de opciones que contiene. Cuando seleccione el nodo de una página determinada, sus opciones aparecen en el área de visualización.

 Las opciones de una característica del IDE no aparecen en el panel de navegación hasta que la característica se carga en la memoria. Por lo tanto, las mismas opciones pueden no mostrarse cuando empieza una sesión que se han mostrado cuando ha finalizado la última. Cuando crea un proyecto o ejecuta un comando que usa una aplicación determinada, los nodos de las opciones relevantes se agregan al cuadro de diálogo Opciones. Estas opciones agregadas seguirán estando disponibles mientras que la característica del IDE siga estando en la memoria.

> [!NOTE]
> Algunas colecciones de configuraciones definen el número de páginas que aparecen en el panel de navegación del cuadro de diálogo Opciones. Puede elegir ver todas las páginas posibles seleccionando **Mostrar todas las configuraciones**.

## <a name="how-options-are-applied"></a>Cómo se aplican las opciones
 Al hacer clic en Aceptar en el cuadro de diálogo **Opciones** se guardan todas las opciones en todas las páginas. Al hacer clic en Cancelar en cualquier página se cancelan todas las solicitudes de cambio, incluidas las que se acaban de realizar en otras páginas de **opciones**. Algunos cambios en la configuración de opciones, como los que se realizan en el [cuadro de diálogo Fuentes y colores, Entorno, Opciones](../../ide/reference/fonts-and-colors-environment-options-dialog-box.md) solo surtirán efecto después de que cierre y vuelva a abrir Visual Studio.

### <a name="show-all-settings"></a>Mostrar todas las configuraciones
 Al seleccionar o anular la selección de **Mostrar todas las configuraciones** se aplican todos los cambios que ha realizado en el cuadro de diálogo **Opciones**, incluso cuando todavía no ha hecho clic en **Aceptar**.

## <a name="see-also"></a>Vea también
 [Personalizar el editor](../../ide/customizing-the-editor.md)
