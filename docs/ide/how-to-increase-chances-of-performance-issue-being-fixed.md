---
title: Aumento de la probabilidad de resolución de un problema de rendimiento
description: Información adicional y procedimientos recomendados para enviar problemas de rendimiento de Visual Studio
ms.custom: SEO-VS-2020
author: madskristensen
ms.author: madsk
manager: jillfra
ms.date: 11/19/2019
ms.topic: conceptual
ms.openlocfilehash: 1567e75d5e0a6f27aee68cd783b9ebd4a70815f4
ms.sourcegitcommit: da7f093db52df5dcd67e0a030e616b307f0dc2a8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/24/2020
ms.locfileid: "91211193"
---
# <a name="how-to-increase-the-chances-of-a-performance-issue-being-fixed"></a>Cómo aumentar la probabilidad de resolución de un problema de rendimiento

La herramienta "[Notificar un problema](./how-to-report-a-problem-with-visual-studio.md?view=vs-2019&preserve-view=true)" es muy usada entre los usuarios de Visual Studio para notificar una serie de problemas. El equipo de Visual Studio detecta las tendencias de bloqueo y lentitud en los comentarios de los usuarios y soluciona los problemas que afectan a un amplio conjunto de usuarios. Cuanto más accionable sea una incidencia de soporte técnico concreta, más probable es que sea diagnosticada y resuelta rápidamente por el equipo del producto. En este documento se describen los procedimientos recomendados para notificar problemas de bloqueo o lentitud a fin de hacerlos más accionables.

## <a name="general-best-practices"></a>Procedimientos recomendados generales

Visual Studio es una plataforma grande y compleja que admite multitud de lenguajes, tipos de proyecto, plataformas, etc. Su rendimiento depende de los componentes instalados y activos en una sesión, de las extensiones instaladas, de la configuración de Visual Studio, de la configuración del equipo y, por último, de la forma del código que se está editando. Dado el número de variables, es difícil saber si el informe de problema de un usuario tiene la misma causa subyacente que un informe de problema de otro usuario, aunque el síntoma visible sea el mismo. Por eso, estos son algunos procedimientos recomendados para asegurarse de que el informe de problema específico tenga mayor probabilidad de ser diagnosticado.

**Proporcione un título lo más específico posible**

Busque firmas distintivas para el problema que se está notificando e incluya lo máximo posible en el título. Si el título es descriptivo, es menos probable que los usuarios con problemas no relacionados (pero el mismo síntoma superficial) voten o comenten la incidencia, lo que dificulta el diagnóstico *del* problema.

**En caso de duda, registre un nuevo informe de problema**

Muchos problemas pueden no tener ninguna firma ni pasos distintivos que reproducir. En estos casos, un nuevo informe es mejor que un voto o un comentario en otro informe que notifique un *síntoma* externo similar. En función del tipo de informe, incluya archivos de diagnóstico adicionales en él, como se indica más adelante en este documento.

**Procedimientos recomendados específicos del problema**

A continuación se describen los problemas que resultan difíciles de diagnosticar sin buenos archivos de diagnóstico. Después de identificar el caso que mejor describe un problema, siga los pasos de comentarios específicos de ese caso.

- [Bloqueos:](#crashes) un bloqueo se produce cuando el proceso (Visual Studio) finaliza de forma inesperada.

- [Falta de respuesta:](#unresponsiveness) VS deja de responder durante un largo período de tiempo.

- [Problemas de lentitud:](#slowness-and-high-cpu-issues) cualquier acción específica en VS es más lenta de lo deseado.

- [Uso de CPU elevado:](#slowness-and-high-cpu-issues) periodos prolongados de uso de CPU inesperadamente elevado.

- [Problemas de fuera de proceso:](#out-of-process-issues) Un problema causado por un proceso satélite de Visual Studio

## <a name="crashes"></a>Bloqueos
Un bloqueo se produce cuando el proceso (Visual Studio) finaliza de forma inesperada.

**Bloqueos reproducibles directamente**

Los bloqueos reproducibles directamente son casos que tienen todas las características siguientes:

- Se pueden observar si se sigue un conjunto conocido de pasos

- Se pueden observar en varios equipos (si están disponibles)

- Se pueden reproducir en código de ejemplo o en un proyecto que se puede asociar a los comentarios o proporcionarse como parte de estos (si los pasos implican abrir un proyecto o un documento)

En el caso de estos problemas, siga los pasos de "[Cómo notificar un problema](./how-to-report-a-problem-with-visual-studio.md)" y asegúrese de incluir:

- Los pasos para reproducir el problema

- Un proyecto de reproducción independiente, como se ha descrito anteriormente. Si la reproducción independiente no es posible, incluya:

  - El lenguaje de los proyectos abiertos (C\#, C++, etc.)

  - El tipo de proyecto (aplicación de consola, ASP.NET, etc.)

> [!NOTE]
> **Comentarios más valiosos:** en este caso, los comentarios más valiosos son el conjunto de pasos para reproducir el problema junto con el código fuente de ejemplo.

**Bloqueos desconocidos**

Si no está seguro de lo que está causando los bloqueos o parecen aleatorios, puede capturar volcados localmente cada vez que Visual Studio se bloquee y adjuntarlos para separar los elementos de comentarios. Para guardar volcados localmente cuando se bloquea Visual Studio, ejecute los siguientes comandos en una ventana de comandos de administrador:

```
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\devenv.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService32.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"

reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpType /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpCount /t REG_DWORD /d 2
reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\Windows Error Reporting\LocalDumps\ServiceHub.RoslynCodeAnalysisService.exe" /v DumpFolder /t REG_SZ /d "C:\CrashDumps"
```

Personalice el recuento de volcados y la carpeta de volcados según corresponda. Puede obtener más información sobre esta configuración [aquí](/windows/win32/wer/collecting-user-mode-dumps).

> [!NOTE]
> Los volcados capturados mediante el administrador de tareas probablemente tengan el valor de bits incorrecto, lo que los hace menos útiles. El procedimiento descrito anteriormente es el método preferido para capturar un volcado del montón. Si quiere usar el administrador de tareas, cierre el que se está ejecutando en ese momento, inicie el administrador de tareas de 32 bits (%windir%\\syswow64\\taskmgr.exe) y recopile un volcado del montón desde ahí.

> [!NOTE]
> Cada archivo de volcado generado mediante este método tiene un tamaño de hasta 4 GB. Asegúrese de establecer la carpeta de volcados en una ubicación con el espacio de unidad adecuado o ajuste el recuento de volcados correctamente.

Cada vez que Visual Studio se bloquea, se crea un archivo de volcado **devenv.exe.[number].dmp** en la ubicación configurada.

Luego use la característica "Notificar un problema..." de Visual Studio. Esta le permite adjuntar el volcado adecuado.

1. Busque el archivo de volcado del bloqueo que está notificando (busque un archivo con la hora de creación correcta).

2. Si es posible, comprima el archivo (\*.zip) para reducir su tamaño antes de enviar los comentarios.

3. Siga los pasos de "[Cómo notificar un problema](./how-to-report-a-problem-with-visual-studio.md)" y adjunte el volcado del montón a un nuevo elemento de comentarios.

> [!NOTE]
> **Comentarios más valiosos:** en este caso, la información más valiosa es el volcado del montón capturado en el momento del bloqueo.

## <a name="unresponsiveness"></a>Falta de respuesta
VS deja de responder durante un largo período de tiempo.

**Falta de respuesta reproducible directamente**

Como se ha descrito en la sección correspondiente sobre bloqueos, en el caso de los problemas que se pueden reproducir fácilmente, se observan en varios equipos y se pueden mostrar en un pequeño ejemplo, los informes de comentarios más valiosos son aquellos que incluyen pasos para reproducir el problema y código fuente de ejemplo que muestra el problema.

**Falta de respuesta desconocida**

Si una falta de respuesta se manifiesta de un modo imprevisible, en la siguiente repetición inicie una nueva instancia de Visual Studio y notifique un problema desde esa instancia.
En la pantalla "Grabar", asegúrese de seleccionar la sesión de Visual Studio que no responde. (Para obtener más información acerca de cómo registrar acciones que podamos seguir para reproducir el problema, consulte el paso 8 en la página [Cómo notificar un problema](./how-to-report-a-problem-with-visual-studio.md)).

Si la instancia de Visual Studio que no responde se ha iniciado en modo de administrador, la segunda instancia también debe iniciarse en este modo.

>[!NOTE]
> **Comentarios más valiosos:** en este caso, la información más valiosa es el volcado del montón capturado en el momento de la falta de respuesta.

## <a name="slowness-and-high-cpu-issues"></a>Problemas de lentitud y uso de CPU elevado

Lo que hace que un problema de lentitud o uso de CPU elevado sea más accionable es un seguimiento de rendimiento capturado mientras está en curso la operación lenta o el evento con un uso de CPU elevado.

>[!NOTE]
> Si es posible, aísle cada escenario en un informe de comentarios específico independiente.
Por ejemplo, si la escritura y la navegación son lentos, siga los pasos siguientes una vez por problema. Esto ayuda al equipo del producto a aislar la causa de problemas concretos.

Para obtener los mejores resultados posibles al capturar el rendimiento, siga estos pasos:

1. Si aún no se está ejecutando, tenga abierta una copia de Visual Studio en la que va a reproducir el problema.

    - Tenga todo configurado para reproducir el problema. Por ejemplo, si necesita que haya un proyecto determinado cargado con un archivo específico abierto, asegúrese de que ambos pasos se hayan completado antes de continuar.

    - Si *no* está notificando un problema específico de la carga de una solución, intente esperar entre 5 y 10 minutos (o más, según el tamaño de la solución) después de abrirla antes de grabar el seguimiento de rendimiento. El proceso de carga de una solución produce una gran cantidad de datos, por lo que esperar unos minutos ayuda al equipo a centrarse en el problema concreto que está notificando.

2. Inicie una segunda copia de Visual Studio *sin ninguna solución abierta*.

3. En la nueva copia de Visual Studio, abra la herramienta **Notificar un problema**.

4. Siga los pasos de [Cómo notificar un problema](./how-to-report-a-problem-with-visual-studio.md) hasta que llegue al paso "Proporcionar un seguimiento y un volcado del montón (opcional)".

5. Elija grabar la primera copia de Visual Studio (la del problema de rendimiento) e inicie la grabación.

    - Aparece la aplicación Grabación de acciones de usuario y comienza la grabación.

    - **Durante la grabación**, realice la acción problemática en la primera copia de Visual Studio. Para el equipo resulta difícil corregir problemas de rendimiento específicos si no aparecen dentro del tiempo grabado.

    - Si la acción es inferior a 30 segundos y se puede repetir con facilidad, repita la acción para mostrar más el problema.

    - En la mayoría de los casos, un seguimiento de 60 segundos es suficiente para mostrar los problemas, especialmente si la acción problemática ha durado (o se ha repetido) durante más de 30 segundos. La duración se puede ajustar según sea necesario para capturar el comportamiento que se quiere corregir.

6. Haga clic en "Detener grabación" en la Grabadora de acciones de usuario en cuanto finalice la operación lenta o el evento de uso de CPU elevado que quiere notificar. El procesamiento del seguimiento de rendimiento puede tardar unos minutos.

7. Una vez terminado, hay varios adjuntos para los comentarios. Adjunte cualquier archivo adicional que pueda ayudar a reproducir el problema (un proyecto de ejemplo, capturas de pantallas, vídeos, etc.).

8. Envíe los comentarios.

Al grabar un seguimiento de rendimiento, si la operación lenta o el uso de CPU elevado que notifica termina, detenga inmediatamente la grabación. Si se recopila demasiada información, se sobrescribe la información más antigua. Si el seguimiento no se detiene pronto (en unos segundos) tras la operación interesante, se sobrescriben datos de seguimiento de utilidad.

No adjunte directamente seguimientos de rendimiento a elementos de comentarios existentes en el sitio web Developer Community. La solicitud o entrega de información adicional es un flujo de trabajo admitido en la herramienta Notificar un problema integrada de Visual Studio. Si se requiere un seguimiento de rendimiento para resolver un elemento de comentarios anterior, se establece el estado del elemento de comentarios en "Se necesita más información", y se puede responder de la misma manera que al notificar un problema nuevo. Para obtener instrucciones detalladas, vea la sección ["Se necesita más información"](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed) del documento de la herramienta Notificar un problema.

> [!NOTE]
> **Comentarios más valiosos:** en casi todos los problemas de uso de CPU elevado y lentitud, los comentarios más valiosos son una descripción general de lo que se intentaba hacer, junto con el seguimiento de rendimiento (\*.etl.zip) que captura el comportamiento durante ese momento.

**Seguimientos de rendimiento avanzados**

Las capacidades de recopilación de seguimiento de la herramienta Notificar a problema bastan para la mayoría de los escenarios. Pero hay ocasiones en las que se necesita más control sobre la recopilación de seguimiento (por ejemplo, un seguimiento con un tamaño de búfer mayor), en cuyo caso PerfView es una herramienta excelente. Los pasos para grabar manualmente el seguimiento de rendimiento mediante la herramienta PerfView se pueden encontrar en la página [Grabación de seguimientos de rendimiento con PerfView](https://github.com/dotnet/roslyn/blob/master/docs/wiki/Recording-performance-traces-with-PerfView.md).

## <a name="out-of-process-issues"></a>Problemas de fuera de proceso

> [!NOTE]
> A partir de la versión 16.3 de Visual Studio 2019, los registros fuera de proceso se adjuntan automáticamente a los comentarios enviados mediante la herramienta notificar un problema.
Sin embargo, si el problema se puede reproducir directamente, seguir los pasos siguientes podría ayudar a agregar información adicional para ayudar a diagnosticar mejor el problema.

Hay una serie de procesos satélite que se ejecutan en paralelo con Visual Studio y proporcionan varias características fuera del proceso principal de Visual Studio. Si se produce un error en uno de estos procesos satélite, normalmente se verá en el lado de Visual Studio como 'StreamJsonRpc.RemoteInvocationException' o 'StreamJsonRpc.ConnectionLostException'.

Lo que hace que estos tipos de problemas sean más útiles es proporcionar registros adicionales que se pueden recopilar siguiendo estos pasos:

1. Si se trata de un problema reproducible directamente, empiece por eliminar la carpeta **%Temp%/servicehub/logs**. Si no puede reproducir este problema, mantenga esta carpeta intacta y omita las siguientes viñetas:

    - Establezca la variable de entorno global **ServiceHubTraceLevel** en **All** (Todo).
    - Reproduzca el problema.

2. Descargue [aquí](https://www.microsoft.com/download/details.aspx?id=12493) la herramienta de recopilación de registros de Microsoft Visual Studio y .NET Framework.
3. Ejecute la herramienta. Esto genera un archivo zip en **%temp%/vslogs.zip**. Adjunte el archivo a sus comentarios.

## <a name="see-also"></a>Vea también

* [Opciones de comentarios de Visual Studio](../ide/feedback-options.md)
* [Notificación de un problema con Visual Studio para Mac](/visualstudio/mac/report-a-problem)
* [Notificación de un problema con C++](/cpp/how-to-report-a-problem-with-the-visual-cpp-toolset)
* [Comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/)
* [Privacidad de datos de la Comunidad de desarrolladores](developer-community-privacy.md)