---
title: Depuración de código de GPU | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
ms.assetid: c7e77a5a-cb57-4b11-9187-ecc89acc8775
caps.latest.revision: 23
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c57fab57b4f9baf24212e2806d6d4acd913dff91
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "82586737"
---
# <a name="debugging-gpu-code"></a>Depuración de código de GPU
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Puede depurar el código de C++ que se está ejecutando en la unidad central de gráficos (GPU). La compatibilidad con la depuración de GPU en Visual Studio incluye la detección de carrera, el inicio de procesos y su asociación y la integración en las ventanas de depuración.  
  
## <a name="supported-platforms"></a>Plataformas compatibles  
 La depuración se admite en [!INCLUDE[win7](../includes/win7-md.md)], [!INCLUDE[win8](../includes/win8-md.md)], [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)], y [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Para depurar en el emulador de software, se requiere [!INCLUDE[win8](../includes/win8-md.md)] o [!INCLUDE[winserver8](../includes/winserver8-md.md)]. Para depurar en el hardware, debe instalar los controladores de su tarjeta gráfica. No todos los proveedores de hardware implementan todas las características del depurador. Vea la documentación del proveedor para conocer las limitaciones.  
  
> [!NOTE]
> Los proveedores de hardware independientes que deseen admitir la depuración de GPU en Visual Studio deben crear un archivo DLL que implemente la interfaz VSD3DDebug y esté diseñado para sus propios controladores.  
  
## <a name="configuring-gpu-debugging"></a>Configurar la depuración de GPU  
 El depurador no puede interrumpir el código de CPU y el código de GPU en la misma ejecución de la aplicación. De forma predeterminada, el depurador interrumpe el código de CPU. Para depurar el código de GPU, siga uno de estos dos pasos:  
  
- En la lista **Depurar tipo** de la barra de herramientas **Estándar**, elija **Solo GPU**.  
  
- En el **Explorador de soluciones**, en el menú contextual del proyecto, elija **Propiedades**. En el cuadro de diálogo **Páginas de propiedades**, seleccione **Depuración** y después elija **Solo GPU** en la lista **Tipo de depurador**.  
  
## <a name="launching-and-attaching-to-applications"></a>Iniciar y asociar a aplicaciones  
 Puede utilizar los comandos de depuración de Visual Studio para iniciar y detener la depuración de GPU. Vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md) para obtener más información. También puede asociar el depurador de GPU a un proceso en ejecución, pero únicamente si dicho proceso ejecuta código de GPU. Para obtener más información, vea [Asociar con procesos en ejecución con el depurador de Visual Studio](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
## <a name="run-current-tile-to-cursor-and-run-to-cursor"></a>Ejecutar Tile actual hasta el cursor y Ejecutar hasta el cursor  
 Al depurar en la GPU, tiene dos opciones para ejecutar hasta la ubicación del cursor. Los comandos de ambas opciones están disponibles en el menú contextual del editor de código.  
  
1. El comando **Ejecutar hasta el cursor** ejecuta la aplicación hasta que llega a la ubicación del cursor y, después, se interrumpe. Esto no implica que el subproceso actual se ejecute hasta el cursor; más bien significa que el primer subproceso que alcanza la ubicación del cursor desencadena la interrupción. Vea [Desplazarse por el código con el depurador](../debugger/navigating-through-code-with-the-debugger.md).  
  
2. El comando **Ejecutar Tile actual hasta el cursor** ejecuta la aplicación hasta que todos los subprocesos del icono actual alcanzan el cursor y, después, se interrumpe.  
  
## <a name="debugging-windows"></a>Ventanas de depuración  
 Mediante determinadas ventanas de depuración, puede examinar, marcar e inmovilizar subprocesos de GPU. Para obtener más información, consulte:  
  
- [Uso de la ventana Pilas paralelas](../debugger/using-the-parallel-stacks-window.md)  
  
- [Usar la ventana Tareas](../debugger/using-the-tasks-window.md)  
  
- [Cómo: Uso de la ventana Inspección paralela](../debugger/how-to-use-the-parallel-watch-window.md)  
  
- [Herramientas para depurar subprocesos y procesos en Visual Studio](../debugger/debug-threads-and-processes.md) (barra de herramientas Ubicación de depuración)  
  
- [Cómo: usar la ventana Subprocesos de GPU](../debugger/how-to-use-the-gpu-threads-window.md)  
  
## <a name="data-synchronization-exceptions"></a>Excepciones de la sincronización de datos  
 El depurador puede identificar varias condiciones de sincronización de datos durante la ejecución. Cuando se detecta una condición, el depurador entra en el estado de interrupción. Tiene dos opciones: **Interrumpir** o **Continuar**. Mediante el cuadro de diálogo **Excepciones**, puede configurar si el depurador detectará estas condiciones y también para qué condiciones se interrumpirá. Para obtener más información, vea [Administración de excepciones con el depurador](../debugger/managing-exceptions-with-the-debugger.md). También puede usar el cuadro de diálogo **Opciones** para especificar que el depurador debe omitir las excepciones si los datos escritos no cambian el valor de los datos. Para obtener más información, consulta [General, Debugging, Options Dialog Box](../debugger/general-debugging-options-dialog-box.md).  
  
## <a name="troubleshooting"></a>Solución de problemas  
  
### <a name="specifying-an-accelerator"></a>Especificar un acelerador  
 Los puntos de interrupción del código de GPU solo se visitan si el código se ejecuta en el acelerador [accelerator::direct3d_ref](https://msdn.microsoft.com/library/a514b1a7-3b3f-4011-be6c-f7b0d9a42663) (REF). Si no especifica un acelerador en el código, el acelerador REF se selecciona automáticamente como el **Tipo de acelerador de depuración** en las propiedades del proyecto. Si el código selecciona explícitamente un acelerador, el acelerador REF no se usará durante la depuración y los puntos de interrupción no se visitarán a menos que el hardware de GPU sea compatible con la depuración. Puede resolverlo escribiendo código para que utilice el acelerador REF durante la depuración. Para obtener más información, consulte las propiedades del proyecto, así como [Uso de los objetos accelerator y accelerator_view](https://msdn.microsoft.com/library/18f0dc66-8236-4420-9f46-1a14f2c3fba1) y [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="conditional-breakpoints"></a>Puntos de interrupción condicionales  
 Se admiten puntos de interrupción condicionales en el código de GPU, pero no todas las expresiones se pueden evaluar en el dispositivo. Cuando una expresión no se puede evaluar en el dispositivo, se evalúa en el depurador. Es probable que el depurador se ejecute más despacio que el dispositivo.  
  
### <a name="error-there-is-a-configuration-issue-with-the-selected-debugging-accelerator-type"></a>Error: problema de configuración con el tipo de acelerador de depuración seleccionado.  
 Este error se produce cuando existe una incoherencia entre la configuración del proyecto y la configuración del equipo en el que está depurando. Para obtener más información, vea [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md).  
  
### <a name="error-the-debug-driver-for-the-selected-debugging-accelerator-type-is-not-installed-on-the-target-machine"></a>Error: el controlador de depuración del tipo de acelerador de depuración seleccionado no está instalado en la máquina de destino.  
 Este error se produce si está depurando en un equipo remoto. El depurador no puede determinar si los controladores están instalados en el equipo remoto hasta el momento de la ejecución. Los controladores los suministra el fabricante de la tarjeta gráfica.  
  
### <a name="error-timeout-detection-and-recovery-tdr-must-be-disabled-at-the-remote-site"></a>Error: la función de detección del tiempo de espera y recuperación (TDR) debe estar deshabilitada en el sitio remoto.  
 Es posible que para los cálculos de C++ AMP se supere el intervalo de tiempo predeterminado establecido por la detección de tiempo de espera de Windows y el proceso de recuperación (TDR). Cuando ocurre esto, se cancela el cálculo y se pierden los datos. Para obtener más información, vea [Control de los TDR en C++ AMP](https://blogs.msdn.com/b/nativeconcurrency/archive/2012/03/07/handling-tdrs-in-c-amp.aspx).  
  
## <a name="see-also"></a>Consulte también  
 [Tutorial: depurar una aplicación C++ AMP](https://msdn.microsoft.com/library/40e92ecc-f6ba-411c-960c-b3047b854fb5)   
 [Configuración del proyecto para una configuración de depuración de C++](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Iniciar la depuración de GPU en Visual Studio](https://docs.microsoft.com/archive/blogs/nativeconcurrency/start-gpu-debugging-in-visual-studio-2012)
