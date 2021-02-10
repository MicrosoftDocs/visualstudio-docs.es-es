---
title: General, Entorno, Opciones (Cuadro de diálogo)
description: Obtenga información sobre cómo usar la página General de la sección Entorno para cambiar los temas de color, la configuración de la barra de estado, las asociaciones de extensión de archivo, etc., para el IDE.
ms.custom: SEO-VS-2020
ms.date: 07/26/2019
ms.topic: reference
f1_keywords:
- VS.Environment.General
- VS.Message.0x800a002e
- VS.OptionsDialog.Environment
- VS.ToolsOptionsPages.Environment
- VS.ToolsOptionsPages.Environment.General
helpviewer_keywords:
- recently used file lists
- Windows menu, customizing
- status bar, displaying
- Options dialog box, General Environment
- General Environment Options dialog box
- Environment Options dialog box
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b58cf19406d49c175a07ab5e3dad60fd0354c656
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99969703"
---
# <a name="options-dialog-box-environment--general"></a>Cuadro de diálogo Opciones: Entorno \> General

Use esta página para cambiar, entre otras opciones, los temas de color, la configuración de la barra de estado y las asociaciones de las extensiones de archivo del entorno de desarrollo integrado (IDE). Para acceder al cuadro de diálogo **Opciones**, abra el menú **Herramientas**, pulse **Opciones**, abra la carpeta **Entorno** y pulse la página **General**.

## <a name="visual-experience"></a>Experiencia visual

**Tema de color**

Elija el tema de color **Azul**, **Claro**, **Oscuro** o **Azul (contraste adicional)** para el IDE.

Puede instalar temas predefinidos adicionales y crear temas personalizados si descarga e instala **Visual Studio Color Theme Editor** desde [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=VisualStudioPlatformTeam.VisualStudio2017ColorThemeEditor). Después de instalar esta herramienta, aparecerán temas de color adicionales en el cuadro de lista **Tema de color**.

**Aplicar tipografía de título a la barra de menús**

De manera predeterminada, los menús usan la tipografía de título. Desactive esta opción para usar solo mayúsculas.

::: moniker range=">=vs-2019"

**Optimizar la representación de las pantallas con densidades de píxeles distintas (requiere reiniciar)**

Esta opción habilita o deshabilita la distinción de puntos por pulgada (ppp) por monitor (o *PMA*). Cuando se habilita PMA, la interfaz de usuario de Visual Studio aparece nítida en la configuración de ppp y factor de escala de cualquier monitor, incluso en varios monitores. Para habilitar PMA, necesita la actualización de abril de 2018 de Windows 10 o posterior y .NET Framework 4.8 o posterior. (Esta opción aparece atenuada si no se cumplen estos dos requisitos previos).

> [!TIP]
> - Windows 10 tiene una opción que dice **Permitir que Windows intente corregir las aplicaciones para que no se vean borrosas**. La **activación** de esa configuración de Windows tiene un efecto insignificante si la opción **Optimizar la representación de las pantallas con densidades de píxeles distintas** está marcada.
> - Windows 10 también incluye un **Solucionador de problemas de compatibilidad de programas**. No se recomienda intentar corregir la apariencia de Visual Studio con dicho solucionador.

::: moniker-end

**Ajustar automáticamente la experiencia visual según rendimiento del cliente**

Especifica si Visual Studio establece el ajuste de forma automática en la experiencia visual o si dicho ajuste debe establecerse explícitamente. Este ajuste puede cambiar la presentación de los colores de degradados a colores planos o restringir el uso de animaciones en los menús o ventanas emergentes.

::: moniker range="vs-2017"

> [!TIP]
> Windows 10 tiene una opción que dice **Permitir que Windows intente corregir las aplicaciones para que no se vean borrosas**. Se recomienda **activar** dicha configuración si Visual Studio aparece borroso en el monitor. Considere la posibilidad de actualizar a [Visual Studio 2019](https://visualstudio.microsoft.com/downloads), que ha mejorado significativamente la claridad de presentación, porque se trata de una aplicación que reconoce los puntos por pulgada por monitor.

::: moniker-end

**Habilitar la experiencia mejorada del cliente**

Habilita la experiencia visual completa de Visual Studio, incluidos los degradados y las animaciones. Desactive esta opción cuando se usen conexiones de Escritorio remoto o adaptadores gráficos más antiguos, ya que estas características pueden tener un rendimiento deficiente en esos casos. Esta opción solo está disponible cuando se desactiva la opción **Ajustar automáticamente la experiencia visual según el cliente**.

**Usar aceleración de gráficos mediante hardware si está disponible**

Usa la aceleración de gráficos mediante hardware si está disponible, en lugar de la aceleración mediante software.

## <a name="other"></a>Otros

**Elementos para mostrar en el menú Ventana**

Personaliza el número de ventanas que aparecen en la lista Ventanas del menú **Ventana**. Especifique un número comprendido entre 1 y 24. El valor predeterminado es 10.

**Elementos mostrados en las listas de los usados recientemente**

Personaliza el número de proyectos y archivos usados más recientemente que aparecen en el menú **Archivo**. Especifique un número comprendido entre 1 y 24. El valor predeterminado es 10. Se trata de una manera fácil de recuperar los proyectos y archivos usados recientemente.

**Mostrar barra de estado**

Muestra la barra de estado. La barra de estado se encuentra en la parte inferior de la ventana del IDE y muestra información sobre el progreso de las operaciones en curso.

**El botón Cerrar afecta solo a la ventana de herramientas activa**

Especifica que, cuando se hace clic en el botón **Cerrar**, solo se cierra la ventana de herramientas que tiene el foco, no todas las ventanas de herramientas del conjunto acoplado. Esta opción se encuentra activada de forma predeterminada.

**Ocultar automáticamente solo afecta a la ventana de la herramienta activa**

Especifica que, cuando se hace clic en el botón **Ocultar automáticamente**, solo se oculta automáticamente la ventana de herramientas que tiene el foco, no todas las ventanas de herramientas del conjunto acoplado. De forma predeterminada, esta opción no está seleccionada.

## <a name="see-also"></a>Vea también

- [Personalizar los diseños de ventana](../../ide/customizing-window-layouts-in-visual-studio.md)
