---
title: "Resultados (Ventana) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.build.output"
  - "vs.debug.output"
  - "vs.output"
helpviewer_keywords: 
  - "Ventana de salida, acerca de la ventana de salida"
  - "Resultados (ventana)"
  - "Cuadro de herramientas, quitar controles"
ms.assetid: d8931d88-250e-4db4-963f-2c5b3e99b45f
caps.latest.revision: 30
caps.handback.revision: 30
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Resultados (Ventana)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La ventana de **salida** puede mostrar mensajes de estado de diversas características del entorno de desarrollo integrado \(IDE\).  Para abrir la ventana **Salida** , en la barra de menú, elija **View\/Output** \(o haga clic en CTRL \+ ALT \+ OR\).  
  
> [!WARNING]
>  La Ventana de salida no aparece en el menú Ver en las ediciones de Visual Studio.  Para traerla hacia arriba, utilice la tecla CTRL de la tecla de acceso rápido \+ ALT \+ B.  
  
## Barra de herramientas  
 **Mostrar resultados desde**  
 Muestra uno o varios paneles de resultados que se pueden ver.  Podrían aparecer varios paneles de información, dependiendo de las herramientas del IDE que haya utilizado la **Ventana de salida** para mostrar mensajes al usuario.  
  
 **Buscar mensaje en el código**  
 Mueve el punto de inserción del editor de código a la línea que contiene el error de compilación seleccionado.  
  
 **Vaya al mensaje anterior**  
 Cambia el foco de la **Ventana de salida** al error de compilación anterior y traslada el punto de inserción del editor de código a la línea que contiene dicho error de compilación.  
  
 **Ir al mensaje siguiente**  
 Cambia el foco de la **Ventana de salida** al error de compilación siguiente y traslada el punto de inserción del editor de código a la línea que contiene dicho error de compilación.  
  
 **Borrar todo**  
 Borra todo el texto del panel **Resultados**.  
  
 **Alternar ajuste de línea**  
 Activa y desactiva la característica de ajuste de línea en el panel **Resultados**.  Cuando está activado el ajuste de línea, el texto de las entradas largas que se extiende más allá del área de visualización se muestra en la línea siguiente.  
  
## Panel Resultados  
 El panel **Resultados** seleccionado en la lista **Mostrar resultados desde** muestra el resultado del origen indicado.  
  
## Enrutar los mensajes a la Ventana de salida  
 Para mostrar la ventana **Salida** siempre que compile un proyecto, en el cuadro **General, Proyectos y soluciones, Opciones** , seleccione **Mostrar ventana de salida cuando empiece la compilación**.  A continuación, con un archivo de código abierto para editar, elija **Ir al mensaje siguiente** y botones **Ir al mensaje anterior** en la barra de herramientas de la ventana **Salida** a entradas seleccionar en el panel **Salida** .  Cuando hace esto, el punto de inserción del Editor de código salta a la línea de código en la que ocurre el problema seleccionado.  
  
 Ciertas características y comandos del IDE invocados en la [Ventana de comandos](../../ide/reference/command-window.md) mandan su resultado a la **Ventana de salida**.  Distribuyen a la salida de herramientas externas como archivos .bat y .com, que se muestra normalmente en la ventana de símbolo del sistema, panel **Salida** cuando selecciona la opción **Usar ventana de salida** en [Administrar herramientas externas](../../ide/managing-external-tools.md).  También se pueden mostrar muchos otros tipos de mensajes en los paneles **Resultados**.  Por ejemplo, cuando la sintaxis Transact\-SQL de un procedimiento almacenado se comprueba con una base de datos de destino, el resultado se muestran en la **Ventana de salida**.  
  
 También puede programar sus propias aplicaciones para escribir mensajes de diagnóstico en tiempo de ejecución en un panel **Resultados**.  Para ello, utilice miembros de la clase <xref:System.Diagnostics.Debug> o la clase <xref:System.Diagnostics.Trace> en el espacio de nombres <xref:System.Diagnostics> de la biblioteca de clases de .NET Framework.  Los integrantes de la clase <xref:System.Diagnostics.Debug> muestran el resultado si se generan configuraciones de Debug de la solución o proyecto; los integrantes de la clase <xref:System.Diagnostics.Trace> muestran el resultado si se generan configuraciones de Debug o de Release.  Para obtener más información, vea [Mensajes de diagnóstico en la ventana de resultados](../../debugger/diagnostic-messages-in-the-output-window.md).  
  
 En [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], puede crear pasos de generación personalizada y eventos de compilación cuyas advertencias y errores se muestren y recuenten en el panel **Resultados**.  Si presiona F1 en una línea de resultado, puede mostrarse un tema de ayuda adecuado.  Para obtener más información, vea [Dar formato a la presentación de un paso de compilación personalizada o un evento de compilación](/visual-cpp/ide/formatting-the-output-of-a-custom-build-step-or-build-event).  
  
## Comportamiento de desplazamiento  
 Si utiliza desplazarse automáticamente en la Ventana de salida y navegar mediante el mouse o con las teclas de dirección, desplazándose automáticamente delimitadores.  Para reanudar el desplazamiento automático, presione CTRL\+FIN.  
  
## Vea también  
 [Mensajes de diagnóstico en la ventana de resultados](../../debugger/diagnostic-messages-in-the-output-window.md)   
 [Cómo: Controlar la ventana Resultados](../Topic/How%20to:%20Control%20the%20Output%20Window.md)   
 [Compilar aplicaciones en Visual Studio](../../ide/compiling-and-building-in-visual-studio.md)   
 [Descripción de las configuraciones de compilación](../../ide/understanding-build-configurations.md)   
 [Información general de la biblioteca de clases](../Topic/.NET%20Framework%20Class%20Library%20Overview.md)