---
title: Deshabilitación del reconocimiento de PPP en Visual Studio
description: Aquí se describen las limitaciones del Diseñador de Windows Forms en monitores HDPI y el procedimiento para ejecutar Visual Studio como un proceso sin reconocimiento de PPP.
ms.date: 04/05/2019
author: jillre
ms.author: jillfra
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: a368108f1b8f9682151ed8c7b0a6d8b83b1b8a1f
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637410"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Deshabilitación del reconocimiento de PPP en Visual Studio

Visual Studio es una aplicación con reconocimiento de puntos por pulgada (PPP), lo que significa que la pantalla se ajusta automáticamente. Si una aplicación indica que no es compatible con PPP, el sistema operativo la escalará como un mapa de bits. Este comportamiento también se denomina virtualización de PPP. La aplicación seguirá creyendo que se está ejecutando al 100 % de la escala, o a 96 ppp.

En este artículo se describen las limitaciones del Diseñador de Windows Forms en monitores HDPI y el procedimiento para ejecutar Visual Studio como un proceso sin reconocimiento de PPP.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Diseñador de Windows Forms en monitores HDPI

El **Diseñador de Windows Forms** en Visual Studio no admite el ajuste de pantalla. Esto provoca problemas de visualización al abrir algunos formularios en el **Diseñador de Windows Forms** en monitores de alta resolución de PPP (HDPI). Por ejemplo, los controles pueden aparecer superpuestos, tal y como se muestra en esta imagen:

![Diseñador de Windows Forms en un monitor HDPI](./media/win-forms-designer-hdpi.png)

Al abrir un formulario en el **Diseñador de Windows Forms** en Visual Studio usando un monitor HDPI, Visual Studio muestra una barra de información amarilla en la parte superior del diseñador:

![Barra de información de Visual Studio para reiniciar en el modo sin reconocimiento de PPP](./media/scaling-gold-bar.png)

El mensaje reza: **El ajuste de escala de la pantalla principal está establecido en el 200 % (192 ppp). Esto puede provocar problemas de representación en la ventana del diseñador.**

> [!NOTE]
> Esta barra de información se incorporó en Visual Studio 2017, versión 15.8.

Si no está trabajando en el Diseñador y no necesita ajustar el diseño del formulario, puede omitir la barra de información y seguir trabajando en el editor de código o en otros tipos de diseñadores. (También puede [deshabilitar las notificaciones](#disable-notifications) para que la barra de información no siga apareciendo). Esto solo afecta al **Diseñador de Windows Forms**. Si necesita trabajar en el **Diseñador de Windows Forms**, la sección siguiente ayuda a [resolver el problema](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Para resolver el problema de visualización

Existen tres opciones para resolver el problema de visualización:

- [Reiniciar Visual Studio como un proceso sin reconocimiento de PPP](#restart-visual-studio-as-a-dpi-unaware-process)
- [Agregar una entrada del Registro](#add-a-registry-entry)
- [Establecer la configuración de ajuste de pantalla en el 100 %](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Reiniciar Visual Studio como un proceso sin reconocimiento de PPP

Para reiniciar Visual Studio como un proceso sin reconocimiento de PPP, seleccione la opción correspondiente en la barra de información amarilla. Esta es la mejor forma de resolver el problema.

Cuando Visual Studio se ejecuta como un proceso sin reconocimiento de PPP, se resuelven los problemas de diseño del diseñador, pero las fuentes pueden aparecer borrosas. Visual Studio muestra un mensaje informativo amarillo diferente cuando se ejecuta como un proceso sin reconocimiento de PPP que reza así: **Visual Studio se está ejecutando como un proceso con reconocimiento de PPP. Puede que los diseñadores WPF y XAML no se muestren correctamente.** La barra de información también proporciona la opción **Reiniciar Visual Studio como un proceso sin reconocimiento de PPP**.

> [!NOTE]
> - Si al seleccionar la opción para reiniciar como un proceso sin reconocimiento de PPP había ventanas de herramientas desacopladas en Visual Studio, puede que la posición de esas ventanas de herramientas cambie.
> - Si usa el perfil de Visual Basic predeterminado, o si no tiene seleccionada la opción **Guardar nuevos proyectos al crearlos** en **Herramientas** > **Opciones** > **Proyectos y soluciones**, Visual Studio no podrá volver a abrir el proyecto cuando se reinicie como un proceso sin reconocimiento de PPP. Sin embargo, puede abrir el proyecto si lo selecciona en **Archivo** > **Proyectos y soluciones recientes**.

Cuando termine de trabajar en el **Diseñador de Windows Forms**, es importante reiniciar Visual Studio como un proceso con reconocimiento de PPP. Cuando se ejecuta como un proceso sin reconocimiento de PPP, las fuentes pueden parecer borrosas y es posible que surjan problemas en otros diseñadores, como el **Diseñador XAML**. Si cierra y vuelve a abrir Visual Studio cuando se está ejecutando en modo sin reconocimiento de PPP, volverá al modo con reconocimiento de PPP. También puede hacer clic en la opción **Reiniciar Visual Studio como un proceso sin reconocimiento de PPP** en la barra de información.

### <a name="add-a-registry-entry"></a>Agregar una entrada del Registro

Para marcar Visual Studio como sin reconocimiento de PPP, se puede modificar el Registro. Abra el **Editor del Registro** y agregue una entrada en la subclave **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers**:

**Entrada**: use uno de estos valores en función de si trabaja con Visual Studio 2017 o 2019:

- C:\Archivos de programa (x86)\Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Archivos de programa (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Si usa la edición Professional o Enterprise de Visual Studio, reemplace **Community** por **Professional** o por **Enterprise** en la entrada. Reemplace también la letra de unidad según sea necesario.

**Tipo**: REG_SZ

**Valor**: DPIUNAWARE

> [!NOTE]
> Visual Studio permanece en modo sin reconocimiento de PPP hasta que quite la entrada del Registro.

### <a name="set-your-display-scaling-setting-to-100"></a>Establecer la configuración de ajuste de pantalla en el 100 %

Para establecer la configuración de ajuste de pantalla en el 100 % en Windows 10, escriba **configuración de pantalla** en el cuadro de búsqueda de la barra de tareas y, después, seleccione **Cambiar configuración de pantalla**. En la ventana **Configuración**, establezca **Cambiar el tamaño del texto, las aplicaciones y otros elementos** en **100 %** .

Puede que no sea conveniente establecer el tamaño de la pantalla en el 100 %, ya que puede hacer que la interfaz de usuario sea demasiado pequeña para usarla.

## <a name="disable-notifications"></a>Deshabilitar las notificaciones

Puede optar por no recibir notificaciones de problemas de ajuste de PPP en Visual Studio. Así, por ejemplo, lo más probable es que quiera deshabilitar las notificaciones si no está trabajando en el diseñador.

Para deshabilitar las notificaciones, en la barra de menús, seleccione **Herramientas** > **Opciones** para abrir el cuadro de diálogo **Opciones**. Después, elija **Diseñador de Windows Forms** > **General** y establezca **Notificaciones de escalado de PPP** en **False**.

![Opción Notificaciones de escalado de PPP en Visual Studio](./media/notifications-option.png)

Si más adelante quiere volver a habilitar las notificaciones de escalado, establezca la propiedad en **True**.

## <a name="troubleshoot"></a>Solucionar problemas

Si la transición de reconocimiento de PPP no funciona según lo previsto en Visual Studio, compruebe si el valor `dpiAwareness` existe en la subclave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** del Editor del Registro. Si existe, elimínelo.

## <a name="see-also"></a>Vea también

- [Ajuste automático de escala en Windows Forms](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
