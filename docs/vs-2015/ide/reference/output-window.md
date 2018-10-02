---
title: Ventana de salida | Microsoft Docs
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vs.build.output
- vs.debug.output
- vs.output
helpviewer_keywords:
- Output window, about Output window
- Output window
- Toolbox, removing controls
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 35
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 6fa3297ca0b3843fcc427bdad4f380828ad441d6
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566232"
---
# <a name="output-window"></a>Resultados (Ventana)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [ventana de salida](https://docs.microsoft.com/visualstudio/ide/reference/output-window).  
  
  
La Ventana de **salida** puede mostrar mensajes de estado de diversas características del entorno de desarrollo integrado (IDE). Para abrir la ventana de **Salida**, en la barra de menús, elija **View/Output** (Vista/Salida) (o haga clic en CTRL + ALT + O).  
  
> [!WARNING]
>  La Ventana de salida no aparece en el menú Ver en las ediciones Express de Visual Studio. Para activarla, use la combinación de teclas CTRL + ALT + O.  
  
## <a name="toolbar"></a>Barra de herramientas  
 **Mostrar resultados desde**  
 Muestra uno o varios paneles de resultados para ver. Puede haber varios paneles de información, según qué herramientas del IDE haya usado la ventana de **salida** para entregar mensajes al usuario.  
  
 **Buscar mensaje en el código**  
 Mueve el punto de inserción en el editor de código a la línea que contiene el error de compilación seleccionado.  
  
 **Ir al mensaje anterior**  
 Cambia el foco de la ventana de **salida** al error de compilación anterior y mueve el punto de inserción en el editor de código a la línea que contiene ese error de compilación.  
  
 **Ir al mensaje siguiente**  
 Cambia el foco de la ventana de **salida** al siguiente error de compilación y mueve el punto de inserción en el editor de código a la línea que contiene ese error de compilación.  
  
 **Borrar todo**  
 Borra todo el texto del panel **Salida**.  
  
 **Alternar ajuste de línea**  
 Activa y desactiva la característica de ajuste automático de línea en el panel **Salida**. Cuando el ajuste automático de línea está activado, el texto de entradas largas que se extiende más allá del área de visualización se muestra en la línea siguiente.  
  
## <a name="output-pane"></a>Panel de salida  
 El panel de **salida** seleccionado en la lista **Mostrar resultados desde** muestra la salida del origen indicado.  
  
## <a name="routing-messages-to-the-output-window"></a>Enrutamiento de mensajes a la Ventana de salida  
 Para mostrar la ventana de **salida** cada vez que compile un proyecto, en el cuadro de diálogo **General, Proyectos y soluciones, Opciones**, seleccione **Mostrar ventana de salida cuando empiece la compilación**. Después, con un archivo de código abierto para su edición, elija los botones **Ir al mensaje siguiente** e **Ir al mensaje anterior** en la barra de herramientas de la ventana de **salida** para seleccionar entradas en el panel de **salida**. Al hacerlo, el punto de inserción en el código salta a la línea de código en que se produce el problema seleccionado.  
  
 Hay determinados comandos y características del IDE que se invocan en la [ventana Comandos](../../ide/reference/command-window.md) que mandan su salida a la ventana de **salida**. La salida de herramientas externas como los archivos .bat y .com, que se muestra normalmente en la ventana de símbolo del sistema, se enruta a un panel de **salida** al seleccionar la opción **Usar ventana de salida** de [Managing External Tools](../../ide/managing-external-tools.md) (Administrar herramientas externas). Se pueden mostrar muchos otros tipos de mensajes los paneles de **salida**. Por ejemplo, cuando se comprueba la sintaxis de Transact-SQL en un procedimiento almacenado con una base de datos de destino, los resultados se muestran en la ventana de **salida**.  
  
 También puede programar sus propias aplicaciones para que escriban mensajes de diagnóstico en tiempo de ejecución en un panel de **salida**. Para hacer esto, use los miembros de la clase <xref:System.Diagnostics.Debug> o de la clase <xref:System.Diagnostics.Trace> en el espacio de nombres <xref:System.Diagnostics> de la biblioteca de clases de .NET Framework. Los miembros de la clase <xref:System.Diagnostics.Debug> muestran la salida al compilar configuraciones de depuración de la solución o proyecto; los miembros de la clase <xref:System.Diagnostics.Trace> muestran la salida al compilar las configuraciones de depuración o lanzamiento. Para obtener más información, consulte [Mensajes de diagnóstico en la ventana de resultados](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 En [!INCLUDE[vcprvc](../../includes/vcprvc-md.md)], puede crear pasos y eventos de compilación personalizados cuyas advertencias y errores se muestran y enumeran en el panel de **salida**. Al pulsar F1 en una línea de salida, puede mostrar un tema de ayuda adecuado. Para obtener más información, consulte [Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación](http://msdn.microsoft.com/library/92ad3e38-24d7-4b89-90e6-5a16f5f998da).  
  
## <a name="scrolling-behavior"></a>Comportamiento de desplazamiento  
 Si usa el desplazamiento automático en la ventana de salida y después se desplaza mediante las teclas de dirección o el mouse, el desplazamiento automático se detiene. Para reanudar el desplazamiento automático, pulse CTRL + Fin.  
  
## <a name="see-also"></a>Vea también  
 [Mensajes de diagnóstico en la ventana de resultados](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Cómo: Controlar la ventana Resultados](http://msdn.microsoft.com/library/91aebd15-8854-4a7a-9f7d-57376fb4e858)   
 [Compilar y generar](../../ide/compiling-and-building-in-visual-studio.md)   
 [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)   
 [Información general de la biblioteca de clases](http://msdn.microsoft.com/library/7e4c5921-955d-4b06-8709-101873acf157)



