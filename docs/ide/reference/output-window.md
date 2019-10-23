---
title: Resultados (Ventana)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 442cac32e0a7103dc573cad707b53ced936c9907
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72655772"
---
# <a name="output-window"></a>Resultados (ventana)

La ventana de **salida** muestra mensajes de estado de diversas características del entorno de desarrollo integrado (IDE). Para abrir la ventana de **Salida**, en la barra de menús, elija **View** > **Output** (Vista/Salida) o presione **Ctrl**+**Alt**+**O**.

## <a name="toolbar"></a>Barra de herramientas

Los controles siguientes se muestran en la barra de herramientas de la ventana de **salida**.

### <a name="show-output-from"></a>Mostrar resultados desde

Muestra uno o varios paneles de resultados para ver. Puede haber varios paneles de información, según qué herramientas del IDE haya usado la ventana de **salida** para entregar mensajes al usuario.

### <a name="find-message-in-code"></a>Buscar mensaje en el código

Mueve el punto de inserción en el editor de código a la línea que contiene el error de compilación seleccionado.

### <a name="go-to-previous-message"></a>Ir al mensaje anterior

Cambia el foco de la ventana de **salida** al error de compilación anterior y mueve el punto de inserción en el editor de código a la línea que contiene ese error de compilación.

### <a name="go-to-next-message"></a>Ir al mensaje siguiente

Cambia el foco de la ventana de **salida** al siguiente error de compilación y mueve el punto de inserción en el editor de código a la línea que contiene ese error de compilación.

### <a name="clear-all"></a>Borrar todo

Borra todo el texto del panel **Salida**.

### <a name="toggle-word-wrap"></a>Alternar ajuste de línea

Activa y desactiva la característica de ajuste automático de línea en el panel **Salida**. Cuando el ajuste automático de línea está activado, el texto de entradas largas que se extiende más allá del área de visualización se muestra en la línea siguiente.

## <a name="output-pane"></a>Panel de salida

El panel de **salida** seleccionado en la lista **Mostrar resultados desde** muestra la salida del origen indicado.

## <a name="route-messages-to-the-output-window"></a>Enrutamiento de mensajes a la ventana Salida

Para mostrar la ventana de **salida** cada vez que compile un proyecto, en el cuadro de diálogo **Opciones**, en la página **Proyectos y soluciones** > **General**, seleccione **Mostrar ventana de salida cuando empiece la compilación**. Después, con un archivo de código abierto para su edición, elija **Ir al mensaje siguiente** e **Ir al mensaje anterior** en la barra de herramientas de la ventana de **salida** para seleccionar entradas en el panel de **salida**. Al hacerlo, el punto de inserción en el código salta a la línea de código en que se produce el problema seleccionado.

Hay determinados comandos y características del IDE que se invocan en la [ventana Comandos](../../ide/reference/command-window.md) que mandan su salida a la ventana de **salida**. La salida de herramientas externas como los archivos *.bat* y *.com*, que se muestra normalmente en la ventana Comandos, se enruta a un panel de **salida** al seleccionar la opción **Usar ventana de salida** en [Administrar herramientas externas](../../ide/managing-external-tools.md). Se pueden mostrar muchos otros tipos de mensajes los paneles de **salida**. Por ejemplo, cuando se comprueba la sintaxis de Transact-SQL en un procedimiento almacenado con una base de datos de destino, los resultados se muestran en la ventana de **salida**.

También puede programar sus propias aplicaciones para que escriban mensajes de diagnóstico en tiempo de ejecución en un panel de **salida**. Para hacer esto, use los miembros de la clase <xref:System.Diagnostics.Debug> o de la clase <xref:System.Diagnostics.Trace> del espacio de nombres <xref:System.Diagnostics> de la API de .NET. Los miembros de la clase <xref:System.Diagnostics.Debug> muestran la salida al compilar configuraciones de depuración de la solución o proyecto; los miembros de la clase <xref:System.Diagnostics.Trace> muestran la salida al compilar las configuraciones de depuración o lanzamiento. Para obtener más información, vea [Mensajes de diagnóstico en la ventana de resultados](../../debugger/diagnostic-messages-in-the-output-window.md).

En C++, puede crear pasos y eventos de compilación personalizados cuyas advertencias y errores se muestran y enumeran en el panel de **salida**. Al presionar **F1** en una línea de salida, puede mostrar un tema de ayuda adecuado. Para obtener más información, vea [Dar formato a la presentación de un paso de compilación personalizada](/cpp/build/formatting-the-output-of-a-custom-build-step-or-build-event).

## <a name="scroll-behavior"></a>Comportamiento de desplazamiento

Si usa el desplazamiento automático en la ventana de **salida** y después se desplaza mediante las teclas de dirección o el mouse, el desplazamiento automático se detiene. Para reanudar el desplazamiento automático, presione **Ctrl**+**Fin**.

## <a name="see-also"></a>Vea también

- [Mensajes de diagnóstico en la ventana de resultados](../../debugger/diagnostic-messages-in-the-output-window.md)
- [Cómo: Controlar la ventana Resultados](https://msdn.microsoft.com/Library/91aebd15-8854-4a7a-9f7d-57376fb4e858)
- [Compilar y generar](../../ide/compiling-and-building-in-visual-studio.md)
- [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)
- [Información general de la biblioteca de clases](/dotnet/standard/class-library-overview)