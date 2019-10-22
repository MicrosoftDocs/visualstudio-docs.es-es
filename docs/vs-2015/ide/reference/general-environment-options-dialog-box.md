---
title: General, Entorno, Opciones (Cuadro de diálogo) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.Message.0x800a002e
- VS.ToolsOptionsPages.Environment.General
- VS.Environment.General
helpviewer_keywords:
- MRU lists
- windows, customizing
- MDI, environment options
- speed, environment animation
- File menu
- menus, customizing
- Windows menu customizing
- status bars, displaying
- Visual Studio Start page, setting
- IDE, startup options
- editors, autocompletion
- Options dialog box, General Environment
- General Environment Options dialog box
ms.assetid: 90fc2e6f-572f-4384-96d8-5678299ce58e
caps.latest.revision: 38
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 83fc6adeba0529be03a9a982713d0584a2a7bc45
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661272"
---
# <a name="general-environment-options-dialog-box"></a>General, Entorno, Opciones (Cuadro de diálogo)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Use esta página para cambiar, entre otras opciones, los temas de color, la configuración de la barra de estado y las asociaciones de las extensiones de archivo del entorno de desarrollo integrado (IDE). Para acceder al cuadro de diálogo **Opciones**, abra el menú **Herramientas**, pulse **Opciones**, abra la carpeta **Entorno** y pulse la página **General**. Si esta página no aparece en la lista, en el cuadro de diálogo **Opciones**, seleccione la casilla **Mostrar todas las configuraciones**.

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, abra el menú **Herramientas** y elija **Importar y exportar configuraciones**. Para obtener más información, vea [Personalizar la configuración de desarrollo en Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="visual-experience"></a>Experiencia visual
 **Tema de color** Elija el tema de color **azul**, **claro** o **oscuro** para el IDE.

 Puede instalar temas predefinidos adicionales y crear temas personalizados si descarga e instala **Visual Studio 2015 Color Theme Editor** desde [Visual Studio Marketplace](https://marketplace.visualstudio.com). Después de instalar esta herramienta, aparecerán temas de color adicionales en el cuadro de lista Tema de color.

 Aplicar el uso de mayúsculas y minúsculas en los menús de la barra de menús está en la **grafía de título** de forma predeterminada en Visual Studio 2015. Desactive esta opción para establecerlos en **MAYÚSCULAS**.

 **Ajustar automáticamente la experiencia visual según el rendimiento del cliente** Especifica si Visual Studio establece el ajuste en la experiencia visual automáticamente o establece el ajuste explícitamente. Este ajuste puede cambiar la presentación de los colores de degradados a colores planos o restringir el uso de animaciones en los menús o ventanas emergentes.

 **Habilitar la experiencia de cliente enriquecida** Habilita la experiencia visual completa de Visual Studio, incluidos los degradados y las animaciones. Desactive esta opción cuando se usen conexiones de Escritorio remoto o adaptadores gráficos más antiguos, ya que estas características pueden tener un rendimiento deficiente en esos casos. Esta opción solo está disponible cuando se desactiva la opción **Ajustar automáticamente la experiencia visual según el cliente**.

 **Usar aceleración de gráficos de hardware Si está disponible** Usa la aceleración de gráficos de hardware Si está disponible, en lugar de la aceleración de software.

## <a name="other"></a>Otro
 **Elementos mostrados en el menú Ventana** Personaliza el número de ventanas que aparecen en la lista Ventanas del menú **Ventana**. Escriba un número comprendido entre 1 y 24. De forma predeterminada, el número es 10.

 **Elementos mostrados en las listas de los usados recientemente** Personaliza el número de proyectos y archivos usados más recientemente que aparecen en el menú **Archivo**. Escriba un número comprendido entre 1 y 24. De forma predeterminada, el número es 10. Se trata de una manera fácil de recuperar los proyectos y archivos usados recientemente.

 **Mostrar barra de estado** Muestra la barra de estado. La barra de estado se encuentra en la parte inferior de la ventana del IDE y muestra información sobre el progreso de las operaciones en curso.

 **El botón Cerrar afecta solo a la ventana de herramientas activa** Especifica que, cuando se hace clic en el botón **Cerrar**, solo se cierra la ventana de herramientas que tiene el foco, no todas las ventanas de herramientas del conjunto acoplado. Esta opción se encuentra activada de forma predeterminada.

 **Ocultar automáticamente solo afecta a la ventana de la herramienta activa** Especifica que, cuando se hace clic en el botón **Ocultar automáticamente**, solo se oculta automáticamente la ventana de herramientas que tiene el foco, no todas las ventanas de herramientas del conjunto acoplado. De forma predeterminada, esta opción no está seleccionada.

 **Administrar asociaciones de archivos** Muestra el cuadro de diálogo **establecer asociaciones de programa de Windows** , donde puede ver las extensiones de archivo de los elementos que suelen estar asociados a Visual Studio y el programa predeterminado actual para abrir cada tipo de archivo. Para hacer que Visual Studio sea la aplicación predeterminada para los tipos de archivos que todavía no tiene asociados, pulse la extensión de archivo y después pulse **Guardar**.

 Esta opción puede ser útil si tiene dos versiones de Visual Studio instaladas en el mismo equipo y posteriormente desinstala una de las versiones. Después de desinstalarla, los iconos de los archivos de Visual Studio ya no aparecerán en el Explorador de archivos. Además, Windows deja de reconocer Visual Studio como la aplicación predeterminada para editar estos archivos. Esta opción restaura esas asociaciones.

## <a name="see-also"></a>Vea también
 [Cuadro de diálogo Opciones de entorno](../../ide/reference/environment-options-dialog-box.md) [personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)
