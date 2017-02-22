---
title: "Crear registradores de reenv&#237;o | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, registradores de reenvío"
  - "MSBuild, registro"
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
caps.latest.revision: 9
caps.handback.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Crear registradores de reenv&#237;o
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Los registradores de reenvío mejoran la eficacia del registro porque permiten elegir los eventos que se desean supervisar al compilar proyectos en un sistema de varios procesadores.  Al habilitar registradores de reenvío, se impide que los eventos no deseados saturen el registrador central, ralenticen el tiempo de compilación y desordenen el registro.  
  
 Para crear un registrador de reenvío, puede implementar la interfaz <xref:Microsoft.Build.Framework.IForwardingLogger> y, a continuación, implementar manualmente sus métodos o bien, utilizar la clase <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> y sus métodos preconfigurados.  \(En la mayoría de las aplicaciones, bastará con la última opción\).  
  
## Registrar eventos y responder a ellos  
 Un registrador de reenvío recopila información acerca de los eventos de compilación a medida que son notificados por el motor de compilación secundario, que es un proceso de trabajo creado por el proceso de compilación principal durante una compilación en un sistema de varios procesadores.  A continuación, el registrador de reenvío selecciona los eventos que se reenviarán al registrador central, en función de las instrucciones proporcionadas.  
  
 Debe registrar los registradores de reenvío para administrar los eventos que desea supervisar.  Para registrar los eventos, los registradores deben invalidar el método <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>.  Ahora, este método incluye un parámetro opcional, `nodecount`, que puede establecerse en el número de procesadores del sistema.  \(De forma predeterminada, el valor es 1.\)  
  
 Los ejemplos de eventos que puede supervisar son <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted>y <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.  
  
 En un entorno de varios procesadores, los mensajes de eventos probablemente no se recibirán en el orden correcto.  Por consiguiente, debe evaluar los eventos utilizando el controlador de eventos del registrador de reenvío y programarlo para determinar qué eventos pasarán al redirector para reenviarlos al registrador central.  Para ello, puede utilizar la clase <xref:Microsoft.Build.Framework.BuildEventContext>, asociada a cada mensaje, para ayudar a identificar los eventos que desea reenviar y, a continuación, pasar los nombres de los eventos a la clase <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> \(o una subclase de ella\).  Con este método no es necesaria ninguna otra codificación para reenviar eventos.  
  
## Especificar un registrador de reenvío  
 Una vez compilado el registrador de reenvío en un ensamblado, debe indicar a [!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] que lo utilice durante las compilaciones.  Para ello, utilice los modificadores `/FileLogger`, `/FileLoggerParameters` y `/DistributedFileLogger` junto con MSBuild.exe.  El modificador `/FileLogger` indica a MSBuild.exe que el registrador se adjunta directamente. El modificador `/DistributedFileLogger` significa que hay un archivo de registro por nodo.  Para establecer los parámetros del registrador de reenvío, utilice el modificador `/FileLoggerParameters`.  Para obtener más información sobre éstos y otros modificadores de MSBuild.exe, vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).  
  
## Registradores para varios procesadores  
 Cuando se compila un proyecto en un sistema de varios procesadores, los mensajes de la compilación de cada procesador no se intercalan automáticamente en una secuencia unificada.  En su lugar, debe establecer una prioridad de agrupación de mensajes mediante la clase <xref:Microsoft.Build.Framework.BuildEventContext> que está asociada a cada mensaje.  Para obtener más información sobre la compilación con varios procesadores, vea [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md).  
  
## Vea también  
 [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)   
 [Registradores de compilación](../msbuild/build-loggers.md)   
 [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)