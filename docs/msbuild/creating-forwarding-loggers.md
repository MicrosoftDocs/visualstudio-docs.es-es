---
title: Crear registradores de reenvío | Microsoft Docs
description: Cree registradores de reenvío de MSBuild para mejorar la eficacia del registro, ya que le permiten elegir los eventos que quiere supervisar al compilar proyectos.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- MSBuild, forwarding loggers
- MSBuild, logging
ms.assetid: 3aebf9c8-b62c-4cb2-b2d6-8cdfcd369a24
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25f8a876ddd4c5c222b608dcea51f98816679181
ms.sourcegitcommit: bd9417123c6ef67aa2215307ba5eeec511e43e02
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/28/2020
ms.locfileid: "92796581"
---
# <a name="create-forwarding-loggers"></a>Crear registradores de reenvío

Los registradores de reenvío mejoran la eficacia del registro, ya que le permiten elegir los eventos que quiere supervisar al compilar proyectos en un sistema de varios procesadores. Al habilitar los registradores de reenvío, puede evitar que eventos no deseados sobrecarguen el registrador central, ralenticen el tiempo de compilación y saturen el registro.

 Para crear un registrador de reenvío, puede implementar la interfaz <xref:Microsoft.Build.Framework.IForwardingLogger> y después implementar manualmente sus métodos, o bien usar la clase <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> y sus métodos preconfigurados. (Esto último será suficiente para la mayoría de las aplicaciones).

## <a name="register-events-and-respond-to-them"></a>Registrar eventos y responder a ellos

 Un registrador de reenvío recopila información sobre los eventos de compilación tal y como los notifica el motor de compilación secundaria, que es un proceso de trabajo que el proceso de compilación principal crea durante una compilación en un sistema de varios procesadores. Después, el registrador de reenvío selecciona los eventos que va a reenviar al registrador central, en función de las instrucciones que se le hayan dado.

 Debe registrar los registradores de reenvío para controlar los eventos que quiere supervisar. Para registrar los eventos, los registradores deben invalidar el método <xref:Microsoft.Build.Utilities.Logger.Initialize%2A>. Este método ahora incluye un parámetro opcional, `nodecount`, que puede establecerse en el número de procesadores del sistema. (De forma predeterminada, el valor es 1).

 Algunos ejemplos de los eventos que puede supervisar son <xref:Microsoft.Build.Framework.IEventSource.TargetStarted>, <xref:Microsoft.Build.Framework.IEventSource.ProjectStarted> y <xref:Microsoft.Build.Framework.IEventSource.ProjectFinished>.

 En un entorno de varios procesadores, es probable que los mensajes de evento se reciban desordenados. Por lo tanto, debe evaluar los eventos mediante el uso del controlador de eventos del registrador de reenvío y programarlo para determinar qué eventos se deben pasar al redirector para realizar el reenvío al registrador central. Para ello, puede usar la clase <xref:Microsoft.Build.Framework.BuildEventContext>, que se adjunta a todos los mensajes, para ayudar a identificar los eventos que quiere reenviar y, después, pasar los nombres de los eventos a la clase <xref:Microsoft.Build.BuildEngine.ConfigurableForwardingLogger> (o a una subclase de ella). Cuando use este método, no se requiere otra codificación específica para reenviar eventos.

## <a name="specify-a-forwarding-logger"></a>Especificar un registrador de reenvío

 Una vez que el registrador de reenvío se ha compilado en un ensamblado, debe indicarle a MSBuild que lo use durante las compilaciones. Para ello, use los modificadores `-FileLogger`, `-FileLoggerParameters` y `-DistributedFileLogger` junto con *MSBuild.exe*. El modificador `-FileLogger` le indica a *MSBuild.exe* que el registrador se adjunta directamente. El modificador `-DistributedFileLogger` significa que hay un archivo de registro por nodo. Para establecer parámetros en el registrador de reenvío, use el modificador `-FileLoggerParameters`. Para obtener más información sobre estos y otros modificadores de *MSBuild.exe* , vea [Referencia de la línea de comandos](../msbuild/msbuild-command-line-reference.md).

## <a name="multi-processor-aware-loggers"></a>Registradores que reconocen varios procesadores

 Cuando se compila un proyecto en un sistema de varios procesadores, los mensajes de compilación de cada procesador no se intercalan automáticamente en una secuencia unificada. Por ello, debe establecer una prioridad de agrupación de mensajes mediante el uso de la clase <xref:Microsoft.Build.Framework.BuildEventContext> adjuntada a cada mensaje. Para obtener más información sobre la compilación con varios procesadores, vea [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md).

## <a name="see-also"></a>Consulte también

- [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)
- [Registradores de compilación](../msbuild/build-loggers.md)
- [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)