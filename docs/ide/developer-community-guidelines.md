---
title: Guía sobre la Comunidad de desarrolladores
description: En este artículo se describen las directrices para trabajar con Visual Studio Developer Community.
ms.date: 6/30/2020
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3e30dcb6a9d65cb562851ed90e350530759975d2
ms.sourcegitcommit: 8a0d0f4c4910e2feb3bc7bd19e8f49629df78df5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/18/2020
ms.locfileid: "97668565"
---
# <a name="developer-community-guidelines"></a>Guía sobre la Comunidad de desarrolladores

Developer Community realiza un seguimiento de las incidencias y las sugerencias de características de Visual Studio.

## <a name="submitting-problems-and-suggestions"></a>Envío de problemas y sugerencias

[Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8) realiza un seguimiento de las incidencias y las sugerencias de características de Visual Studio.

### <a name="before-submitting-an-issue"></a>Antes de enviar una incidencia

Busque su incidencia en Visual Studio Developer Community para asegurarse de que aún no exista. Si ya existe, indique los comentarios pertinentes y registre su voto.

Si para resolver su incidencia necesita realizar una pregunta, formúlela a la comunidad en [Stack Overflow](https://stackoverflow.com/questions/tagged/visual-studio?tab=Newest) mediante la etiqueta _visual-studio_. Contamos con personal de soporte técnico que supervisa esa etiqueta y que le ayudará a solventar las dudas.

Si no encuentra ninguna incidencia que describa el error o la característica que le ocupa, envíe una incidencia siguiendo las directrices que se indican a continuación.

### <a name="writing-a-good-bug-report-or-feature-suggestion"></a>Redacción de un informe de errores o una sugerencia de característica correctos

- Registre solo un problema o solicitud de característica por incidencia.

  - La combinación de varios problemas o solicitudes de características en una sola incidencia dificulta el diagnóstico y puede dar lugar a que otros usuarios no los voten.
  - No agregue la incidencia como comentario a una incidencia existente, a menos que se trate de una entrada idéntica. Muchas incidencias son similares, pero tienen diferentes causas, lo que dificulta el diagnóstico.

- Cuanta más información pueda proporcionar, más fácil nos resultará reproducir y corregir la incidencia.
- Incluya los siguientes pasos con cada incidencia.

  - Pasos reproducibles (1..., 2..., 3...) y una comparación del resultado esperado y el experimentado.
  - Imágenes, animaciones o un vínculo a un vídeo. Las imágenes y las animaciones ilustrarán los pasos de reproducción, pero _no_ los reemplazarán.
  - Según corresponda, incluya un fragmento de código que muestre la incidencia o un vínculo a un repositorio de código que podamos descargar fácilmente en nuestro equipo para recrear la incidencia.

- No olvide seguir estos pasos:

  - Compruebe si la incidencia ya existe. Si es así, vote por la incidencia existente y proporcione comentarios o aclaraciones adicionales según sea necesario.
  - Recree la incidencia después de deshabilitar todas las extensiones. Si detecta que la incidencia la produce una extensión instalada, registre una incidencia sobre la extensión correspondiente.
  - Simplifique el código relacionado con la incidencia, de modo que podamos aislarla mejor.

Incluso en el caso de que una incidencia contenga una descripción detallada, es posible que no podamos reproducirla y que le pidamos más información.

## <a name="managing-problem-reports"></a>Administración de los informes de problemas

La evaluación de prioridades de las incidencias es un proceso de varios pasos que se realiza de forma colaborativa en el equipo de características. La evaluación de prioridades normalmente tarda una semana en completarse, pero puede tardar más tiempo. El objetivo de la evaluación de prioridades es proporcionarle información clara de lo que ocurrirá con su incidencia. Después de esto, por ejemplo, sabrá si planeamos corregir el problema o esperar más comentarios de la comunidad.

Después de notificar un problema, los estados indican en qué punto de su ciclo de vida están sus envíos. Cuando los equipos de producto de Visual Studio revisen sus comentarios, les asignarán un estado. Realice un seguimiento del progreso de los informes de problemas consultando los [estados de problemas y preguntas más frecuentes](./report-a-problem.md).

### <a name="prioritizing-which-issues-to-fix"></a>Prioridad de los problemas que se van a solucionar

No podemos solucionar todos los problemas que se nos comunican. La solución de algunos tiene un costo demasiado alto, la de otros podría retrasar otras áreas de características y la de otros puede tener un impacto demasiado bajo. Sabemos que esto puede desilusionar cuando se ha dedicado tiempo a enviar un informe de problema. Todos nos hemos visto en la misma situación, ya sea en este proyecto o en otros en los que hemos colaborado. Si un problema se ha cerrado y cree que el motivo que hemos dado no es satisfactorio, puede aclarar el caso de uso y solicitar que el problema se vuelva a activar para otra revisión. En este punto, es posible que le pidamos más información.

### <a name="missing-important-information"></a>Información importante que falta

En el caso de que a una incidencia le falte información importante, le asignaremos el estado pertinente para indicar que _se requiere más información_. Agregaremos un comentario en la incidencia con la información específica que necesitamos y recibirá una notificación por correo electrónico. Si no recibimos la información en un plazo de siete días, le enviaremos un recordatorio. Tras ese recordatorio, cerraremos la solicitud después de 14 días de inactividad.

### <a name="other-product"></a>Otro producto

A veces, se informa de incidencias que parecen ser relativas a Visual Studio, pero realmente corresponden a otros productos. Podrían producirse por otra aplicación relacionada o una extensión. 

Cuando esto suceda, se cerrará la incidencia y se le pedirá que la abra con el producto pertinente. Estos son algunos lugares comunes para registrar esas incidencias:

* [SQL Server](https://feedback.azure.com/forums/908035-sql-server)
* [Soporte técnico de Visual Studio Subscription](https://feedback.azure.com/forums/908035-sql-server)
* [Office](https://support.office.com/article/how-do-i-give-feedback-on-microsoft-office-2b102d44-b43f-4dd2-9ff4-23cf144cfb11)
* [Windows](https://support.microsoft.com/help/4021566/windows-10-send-feedback-to-microsoft-with-feedback-hub-app)

#### <a name="additional-information"></a>Información adicional

- [Cómo aumentar la probabilidad de resolución de una incidencia de rendimiento](./how-to-increase-chances-of-performance-issue-being-fixed.md)
- [Solución de problemas y creación de registros para problemas de MSBuild](./msbuild-logs.md)

## <a name="managing-feature-suggestions"></a>Administración de sugerencias de características

Las sugerencias de características son un medio de comunicación entre nosotros y los miembros de la comunidad de desarrolladores. Técnicamente, podríamos mantener todas las solicitudes de características abiertas para siempre. Pero mantener abiertas las incidencias reduciría la visibilidad de la comunidad del estado real de una característica. Por lo tanto, cerramos las solicitudes de características que no abordaremos y asignamos las características que podríamos abordar a la etiqueta _En revisión_.

Si ha sugerido una característica, es posible que le decepcione que no tengamos previsto abordar su solicitud. Lo comprendemos. Todos nos hemos visto en la misma situación (en este proyecto o en otros en los que hayamos contribuido). Así que no se preocupe, valoramos mucho todos sus comentarios. Si cerramos su sugerencia o le asignamos la etiqueta _En revisión_, no se lo tome como algo personal. Si cree que su sugerencia de característica merece estar abierta, aclare el caso de uso y póngase en contacto con nosotros o recopile más votos positivos.

En nuestro proceso de toma de decisiones, tenemos en cuenta los siguientes aspectos en lo que respecta a las sugerencias de características:

- ¿Coincide con nuestra dirección general del producto?
- ¿Nos podemos permitir crearla y mantenerla?
- ¿Se alinea con la estrategia general de nuestra [hoja de ruta](/visualstudio/productinfo/vs-roadmap)?
- ¿Cuenta con el apoyo de la comunidad según los votos y los comentarios?
- ¿Nos encanta a pesar de que no haya tenido mucho éxito en la comunidad?

Si no respondemos afirmativamente a alguna de estas preguntas, la sugerencia se cerrará. No obstante, las sugerencias suelen permanecer abiertas como _En revisión_ para recopilar más comentarios de la comunidad.

Si una sugerencia no coincide con nuestra dirección general del producto, la cerraremos como *Fuera de ámbito*. Por ejemplo, es posible que podamos tener inversiones similares en otros miembros de la familia de productos de Visual Studio. O bien la característica sugerida puede ser pertinente solo para algunas personas, lo que hace que para una extensión sea más sencillo proporcionarla.

Realice un seguimiento del progreso de su sugerencia de característica consultando los [estados de las sugerencias y las preguntas más frecuentes](./report-a-problem.md).

## <a name="discussion-etiquette"></a>Protocolo de debate

Para que la conversación sea clara y transparente, exprésese solo en inglés y comente solo lo relacionado con el problema. Tenga en cuenta a otros usuarios y participe con cortesía y profesionalidad.

Para obtener más información, consulte el [código de conducta de Microsoft Community](https://answers.microsoft.com/en-us/page/codeofconduct).

Cualquier infracción del protocolo de debate puede conllevar la eliminación del comentario y la prohibición de la participación del usuario.

## <a name="data-privacy"></a>Privacidad de datos

Los comentarios y las respuestas son visibles públicamente, pero los archivos adjuntos se comparten de forma privada con Microsoft únicamente. Esto es una ventaja, ya que permite que toda la comunidad pueda ver las incidencias y las soluciones que han encontrado otros usuarios. Pero, si le preocupa la privacidad de sus datos o su identidad, tiene distintas opciones. Obtenga más información sobre la [privacidad de datos de Developer Community](./developer-community-privacy.md).

## <a name="next-steps"></a>Pasos siguientes

Vaya a [Visual Studio Developer Community](https://aka.ms/feedback/suggest?space=8) para informar de problemas, sugerir características o examinar las solicitudes existentes. Disfrútelo.
