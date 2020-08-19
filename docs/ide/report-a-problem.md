---
title: 'Notificación de un problema: estados y preguntas frecuentes'
description: Proporciona información general sobre la herramienta Notificar un problema e incluye definiciones y estados de problemas
ms.date: 11/15/2018
ms.custom: seodec18
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: ca095bf424420fb73ba8f369f7e41daea92fe33d
ms.sourcegitcommit: 98af63c1a53a732558f8207338dc2722abbbe49e
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2020
ms.locfileid: "88584507"
---
# <a name="report-a-problem-states-and-faq"></a>Notificación de un problema: estados y preguntas frecuentes

La herramienta Notificar un problema permite a la Comunidad de desarrolladores de Visual Studio enviar problemas. Cada uno de sus informes de problemas se convierte en un elemento de trabajo en nuestro sistema de ingeniería principal, lo que le permite interactuar directamente con nuestros equipos de producto para ayudarnos a identificar y resolver problemas de gran impacto. Los comentarios enviados con información de diagnóstico muy completa son fundamentales para mejorar la familia de productos de Visual Studio. Agradecemos que dedique tiempo a notificar los problemas.

Además, puede votar los comentarios de otros miembros de la Comunidad para que se le preste más atención a un problema y ayudar a corregirlo con mayor rapidez.

## <a name="problem-status"></a>Estado de problema

Después de notificar un problema, los estados indican en qué punto de su ciclo de vida están sus envíos. Cuando los equipos de Microsoft revisan sus comentarios, les asignan un estado apropiado.  Haga un seguimiento del progreso de los informes del problema consultando los estados que se muestran a continuación, junto con su significado e indicadores de color.

![Estado Nuevo de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/New.jpg)

**Nuevo** indica que se notificó el error o problema recientemente y no se ha tomado ninguna acción relacionada con él todavía.

- - -

![Estado Evaluado de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/Triaged.jpg)

**Evaluado** indica que se completaron los pasos preliminares como moderación, traducción y comprobación inicial de valores duplicados. El vale se ha enrutado al equipo de ingeniería adecuado para que lo tenga en cuenta.

- - -

![Estado Estudiando de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/UnderConsideration.jpg)

**Estudiando** indica que Microsoft está revisando el problema para determinar su impacto para la Comunidad y le dará prioridad en consecuencia. Si el impacto para la Comunidad aún no está claro o no es significativo, seguiremos supervisando el problema en este estado.

- - -

![Estado Bajo investigación de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/UnderInvestigation.jpg)

**Bajo investigación** indica que los ingenieros están investigando activamente el problema para encontrar una solución.

- - -

![Estado Se necesita más información de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/NeedMoreInfo.jpg)

**Se necesita más información** indica que necesitamos más información de diagnóstico para poder avanzar con la investigación.  [Obtenga información sobre cómo responder a las solicitudes Se necesita más información.](./how-to-report-a-problem-with-visual-studio.md#when-further-information-is-needed)

- - -

![Estado Corregido: publicación pendiente de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/FixedPendingRelease.jpg)

**Corregido: publicación pendiente** indica que tenemos una corrección para el problema y estará disponible en una próxima versión preliminar o de lanzamiento.  Cuando la corrección esté disponible en versión preliminar, el problema se etiquetará con "corregido", que especifica la versión preliminar.

- - -

![Estado Cerrado: corregido de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/ClosedFixed.jpg)

**Cerrado: corregido** indica que hemos publicado una corrección para el problema. El problema ahora también tiene una etiqueta "corregido en:" que especifica la versión de lanzamiento.

- - -

![Estado Cerrado: duplicado de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/ClosedDuplicate.jpg)

**Cerrado: duplicado** indica que ya se ha ofrecido información sobre su problema en otros comentarios. Le proporcionaremos el vínculo donde puede realizar el seguimiento del informe del problema original.

- - -

![Estado Cerrado: prioridad baja de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/ClosedLowerPriority.jpg)

**Cerrado: prioridad baja** para centrarnos en dar el mejor valor a cada miembro en nuestra Comunidad de desarrolladores, priorizamos los problemas con el mayor impacto en el cliente. Aunque no podemos resolver este problema concreto en este momento, puede tener la seguridad de que todos sus comentarios son valiosos y ayudan a mejorar Visual Studio.

- - -

![Estado Cerrado: no es un error de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/ClosedNotABug.jpg)

**Cerrado: no es un error** indica que hemos determinado que la característica notificada funciona conforme se espera.

- - -

![Estado Cerrado: no hay suficiente información de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/ClosedNotEnoughInfo.jpg)

**Cerrado: no hay suficiente información** indica que no tenemos información suficiente para investigar esto por usted. Estaremos encantados de reconsiderar los comentarios después de que esté disponible la información necesaria.

- - -

![Estado Cerrado: otro producto de los informes de problemas en la Comunidad de desarrolladores](../ide/media/ProblemStates/ClosedOtherProduct.jpg)

**Cerrado: otro producto** indica que hemos determinado que el problema se aplica a otro producto. Vea el comentario de Microsoft que indica el producto externo y los vínculos relacionados.

- - -

## <a name="faq"></a>Preguntas más frecuentes

### <a name="how-can-i-increase-the-chance-of-my-problem-getting-resolved-quickly"></a>¿Cómo puedo aumentar la posibilidad de que mi problema se resuelva rápidamente?

Se recomienda usar la búsqueda para asegurarse de que aún no existen informes sobre el problema del que está a punto de informar. Si encuentra un elemento existente que coincide con su problema, vote ese vale de problema.

Proporcione toda la información que pueda para ayudar a nuestros equipos a reproducir lo que está experimentando.  Esta información incluye los pasos de reproducción necesarios, fragmentos de código, capturas de pantalla, grabaciones de reproducción, archivos de registro y otros artefactos.  Aquí tiene [información sobre cómo notificar un problema en Visual Studio](./how-to-report-a-problem-with-visual-studio.md).

### <a name="how-is-my-feedback-prioritized"></a>¿Cómo se priorizan mis comentarios?

Hemos recibido mucha información valiosa sobre problemas de nuestros clientes. Para asegurarnos de que proporcionamos el mejor valor a todos los miembros de nuestra Comunidad de desarrolladores, priorizamos la actuación en los comentarios que tiene el mayor impacto de la Comunidad.

Si no podemos responderle personalmente, sepa que apreciamos totalmente sus comentarios. Puede tener la seguridad de que todos sus comentarios llegan al equipo adecuado.

Apreciamos realmente el tiempo que invierte en mejorar Visual Studio.

### <a name="what-actions-can-i-take-if-im-not-satisfied-with-the-resolution"></a>¿Qué puedo hacer si no estoy conforme con la resolución?

Nuestros equipos hacen todo lo posible para diagnosticar y corregir los problemas que experimente, pero puede haber ocasiones en las que nuestra recomendación no le satisfaga plenamente. Vuelva a escribir en los comentarios y háganos saber exactamente con qué no está conforme, e intentaremos hacer todo lo posible para asegurarnos de que se cumplen sus necesidades.

### <a name="how-will-i-get-notified-of-progress-on-my-feedback"></a>¿Cómo obtengo notificaciones del progreso en mis comentarios?

Los equipos de ingeniería de Microsoft se comunicarán con usted respondiendo al vale de comentarios y cambiando el estado de la incidencia a medida que progresen. Recibirá notificaciones de correo electrónico que se envían cuando se publican cambios de estado del vale o se publica una respuesta.  Puede administrar la frecuencia de las notificaciones en la configuración del perfil y las preferencias en el sitio de la Comunidad de desarrolladores.

### <a name="why-cant-i-add-a-problem-for-visual-studio-ide-on-the-developer-community-website"></a>¿Por qué no puedo agregar un problema para el IDE de Visual Studio en el sitio web de la Comunidad de desarrolladores?

La generación de informes sobre un problema mediante Visual Studio permite incluir información de diagnóstico automáticamente en el informe. Es información esencial que proporciona a nuestros ingenieros el contexto que necesitan para comprender totalmente el problema y trabajar para resolverlo.

Al informar a través de Visual Studio, puede compartir fácilmente información de diagnóstico muy completa con nosotros, como archivos de registro grandes, información de bloqueo, capturas de pantalla, grabación de reproducción y otros artefactos que nos ayudan a ofrecerle correcciones de mayor calidad más rápido.
