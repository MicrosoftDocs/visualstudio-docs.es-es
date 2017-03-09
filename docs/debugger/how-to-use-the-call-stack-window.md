---
title: "C&#243;mo: Utilizar la ventana Pila de llamadas | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.callstack"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "SQL"
  - "aspx"
helpviewer_keywords: 
  - "subprocesos [Visual Studio], mostrar llamadas entrantes o salientes"
  - "funciones [depurador], ver código en la pila de llamadas"
  - "código desensamblador"
  - "punto de interrupción, ventana Pila de llamadas"
  - "depurar [Visual Studio], cambiar a otro marco de pila"
  - "depurar [Visual Studio], ventana Pila de llamadas"
  - "Ventana Pila de llamadas, ver código fuente de funciones de la pila de llamadas"
  - "pila, cambiar entre marcos de pila"
  - "Ventana Pila de llamadas, ver código de desensamblado de funciones de la pila de llamadas"
ms.assetid: 5154a2a1-4729-4dbb-b675-db611a72a731
caps.latest.revision: 40
caps.handback.revision: 38
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# C&#243;mo: Utilizar la ventana Pila de llamadas
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Utilizando la ventana **Pila de llamadas**, puede ver las llamadas a las funciones o procedimientos que están actualmente en la pila.  
  
 En la ventana **Pila de llamadas** se muestran el nombre de cada función y el lenguaje de programación en el que se ha escrito.  El nombre de la función o del procedimiento puede ir acompañado de información opcional, por ejemplo el nombre de módulo, número de línea, así como los nombres, tipos y valores de parámetro.  La presentación de esta información opcional se puede activar o desactivar.  
  
 Una flecha amarilla identifica el marco de pila donde está ubicado actualmente el puntero de ejecución.  De forma predeterminada, éste es el marco cuya información aparece en las ventanas Código fuente, **Desensamblado**, **Variables locales**, **Inspección** y **Automático**.  Si desea cambiar el contexto a otro marco en la pila, puede hacerlo en la ventana **Pila de llamadas**.  
  
 Cuando no haya símbolos de depuración disponibles para una parte de una pila de llamadas, la ventana **Pila de llamadas** podría no mostrar información correcta para esa parte de la pila de llamadas.  Aparece la notación siguiente:  
  
 \[Es posible que lo siguientes marcos no estés o sean incorrectos, no se han cargado símbolos para name.dll\]  
  
 En código administrado, de forma predeterminada, la ventana **Pila de llamadas** oculta información del código que no es de usuario.  Aparece la notación siguiente en lugar de la información oculta:  
  
 **\[\<External Code\>\]**  
  
 El código que no es de usuario es cualquier código que no es de tipo "Mi código". Puede elegir mostrar la información de la pila de llamadas del código que no es de usuario mediante el menú contextual.  
  
 Si utiliza el menú contextual, puede elegir ver las llamadas entre subprocesos.  
  
> [!NOTE]
>  Los cuadros de diálogo y los comandos de menú que se ven pueden diferir de los descritos en la Ayuda, dependiendo de los valores de configuración o de edición activos.  Para cambiar la configuración, seleccione **Importar y exportar configuraciones** en el menú **Herramientas**.  Para obtener más información, vea [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/es-es/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Para mostrar la ventana Pila de llamadas \(en modo de interrupción o en modo de ejecución\)  
  
-   En el menú **Depurar**, seleccione **Ventanas** y haga clic en **Pila de llamadas**.  
  
### Para cambiar la información opcional mostrada  
  
-   Haga clic con el botón secundario en la ventana **Pila de llamadas** y establezca o desactive **Mostrar \<***the information that you want***\>**.  
  
### Para mostrar código no definido por usuarios en la ventana Pila de llamadas  
  
-   Haga clic con el botón secundario en la ventana **Pila de llamadas** y seleccione **Mostrar código externo**.  
  
### Para cambiar a otro marco de pila  
  
1.  En la ventana **Pila de llamadas**, haga clic con el botón secundario en el marco cuyo código y datos desee ver.  
  
2.  Seleccione **Cambiar a marco**.  
  
     Una flecha verde con una cola rizada aparece junto al marco que seleccionó.  El puntero de ejecución permanece en el marco original, que sigue marcado con la flecha amarilla.  Si selecciona **Paso** o **Continuar** en el menú **Depurar**, la ejecución continuará en el marco original, no en el seleccionado.  
  
### Para mostrar las llamadas a o desde otro subproceso  
  
-   Haga clic con el botón secundario en la ventana **Pila de llamadas** y seleccione **Incluir llamadas a otros subprocesos o desde estos**.  
  
### Para ver el código fuente de una función de la pila de llamadas  
  
-   En la ventana **Pila de llamadas**, haga clic con el botón secundario en la función cuyo código fuente desee ver y seleccione **Ir a código fuente**.  
  
### Para hacer un seguimiento visual de la pila de llamadas  
  
1.  En la ventana **Pila de llamadas**, abra el menú contextual.  Elija **Mostrar pila de llamadas en mapa de código**. \(Teclado: **CTRL** \+ **MAYÚS** \+ **\`**\)  
  
     Vea [Asignar métodos en la pila de llamadas durante la depuración](../debugger/map-methods-on-the-call-stack-while-debugging-in-visual-studio.md).  
  
### Para ver el código de desensamblado de una función de la pila de llamadas  
  
-   En la ventana **Pila de llamadas**, haga clic con el botón secundario en la función cuyo código de desensamblado desee ver y seleccione **Ir al desensamblado**.  
  
### Para ejecutar una función concreta desde la ventana Pila de llamadas  
  
-   Vea [Ejecutar hasta una ubicación o función determinada](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Run_to_a_specified_location_or_function).  
  
### Para establecer un punto de interrupción en la salida de una llamada a función  
  
-   Vea [Establecer un punto de interrupción en una línea de código fuente, instrucción de ensamblado o función de la pila de llamadas](../debugger/using-breakpoints.md#BKMK_Set_a_breakpoint_at_a_source_line__assembly_instruction__or_call_stack_function_).  
  
### Para cargar los símbolos para un módulo  
  
-   En la ventana **Pila de llamadas**, haga clic con el botón secundario en el módulo cuyos símbolos desee recargar y seleccione **Cargar símbolos**.  
  
## Cargar Símbolos  
 En la ventana **Pila de llamadas**, puede cargar los símbolos de depuración para el código que no los tenga cargados.  Estos símbolos pueden ser .NET Framework o símbolos del sistema descargados de los servidores de símbolos públicos de Microsoft, o símbolos en una ruta de acceso de símbolos en el equipo que está depurando.  
  
 Vea [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md).  
  
#### Para cargar símbolos  
  
1.  En la ventana **Pila de llamadas**, haga clic con el botón secundario en el marco para el cual no están cargados los símbolos.  Se oscurecerá el marco.  
  
2.  Elija **Cargar símbolos desde** y, a continuación, haga clic en **Servidores de símbolos de Microsoft** o **Ruta de acceso de símbolos**.  
  
#### Para configurar la ruta de acceso de símbolos  
  
1.  En la ventana **Pila de llamadas**, elija **Configuración de símbolos** en el menú contextual.  
  
     Se abre el cuadro de diálogo **Opciones** y se muestra la página **Símbolos**.  
  
2.  Haga clic en **Valores de los símbolos**.  
  
3.  En el cuadro de diálogo **Opciones**, haga clic en el icono de carpeta.  
  
     En el cuadro **Ubicaciones del archivo de símbolos \(.pdb\)**, aparece un cursor.  
  
4.  Escriba un nombre de la ruta de acceso del directorio a la ubicación de los símbolos en el equipo que está depurando.  Para la depuración local, éste es su equipo local.  Para la depuración remota, es el equipo remoto.  
  
5.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
## Vea también  
 [Código mixto e información no mostrada en la ventana Pila de llamadas](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md)   
 [Cómo: Cambiar el formato numérico de las ventanas del depurador](../Topic/How%20to:%20Change%20the%20Numeric%20Format%20of%20Debugger%20Windows.md)   
 [Ver datos en el depurador](../debugger/viewing-data-in-the-debugger.md)   
 [Especificar archivos de código fuente y símbolos \(.pdb\)](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [Usar puntos de interrupción](../debugger/using-breakpoints.md)