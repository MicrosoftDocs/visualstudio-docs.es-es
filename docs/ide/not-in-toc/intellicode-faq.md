---
title: Preguntas y respuestas sobre IntelliCode
ms.date: 05/22/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-general
ms.topic: conceptual
manager: douge
author: markw-t
ms.author: mwthomas
ms.openlocfilehash: f0410b3ffd04c42f316d99c150253e72bb1b1944
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 06/04/2018
ms.locfileid: "34468809"
---
# Preguntas más frecuentes de Visual Studio IntelliCode

Gracias por su interés en Visual Studio IntelliCode. Le presentamos algunas preguntas más frecuentes que esperamos que respondan a algunas de las preguntas que puede que tenga.

## P. ¿Qué es Visual Studio IntelliCode?

En la compilación 2018, presentamos Visual Studio IntelliCode, una nueva funcionalidad que mejora el desarrollo de software mediante IA. IntelliCode ayuda a los desarrolladores y a los equipos a programar con confianza, encontrar problemas con mayor rapidez y centrarse en las revisiones del código.

También mostramos una primera vista de cómo IntelliCode mejora el proceso de desarrollo de software de las maneras siguientes:

- Ofrece finalizaciones de código en contexto
- Guía a los desarrolladores para que cumplan con los patrones y estilos de su equipo
- Encuentra problemas de código difíciles de detectar
- Enfoca las revisiones de código, al llamar la atención sobre las áreas que realmente importan

Los desarrolladores pueden buscar más información y registrarse para recibir noticias y obtener versiones preliminares privadas futuras en [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. ¿Qué permite hacer Visual Studio IntelliCode a los clientes?

Visual Studio IntelliCode es una gama de capacidades que ofrece nuevas mejoras de productividad a través de la inteligencia artificial (IA).

Los desarrolladores pueden [descargar una extensión experimental](https://go.microsoft.com/fwlink/?linkid=872707) para Visual Studio 2017, versión 15.7 y posteriores. La extensión proporciona IntelliSense mejorado que predice la API probablemente correcta para que use el desarrollador, en lugar de simplemente presentar una lista alfabética de los miembros. Usa el contexto de código actual y patrones del desarrollador para proporcionar esta lista dinámica. Actualizaremos la extensión con más funcionalidades en los próximos meses.

## P. ¿Hay otras características que se vayan a incorporar a la extensión IntelliCode de Visual Studio? ¿Qué ocurre con la generación de editorconfig?

Estamos trabajando de forma activa en una serie de funcionalidades que estamos ansiosos por compartir públicamente cuando estén disponibles. Hemos mostrado una versión interna inicial de una herramienta que deduce la configuración de editorconfig para el estilo de código y el formato en C# en Microsoft Build 2018. Aún no está en la extensión experimental, pero tenemos previsto que esté disponible pronto. Puede registrarse para recibir noticias y actualizaciones en [https://aka.ms/intellicode](https://aka.ms/intellicode) y ser el primero en enterarse cuando tengamos nuevas funciones disponibles.

## P: ¿Qué hace que "IntelliSense asistido por IA", con la tecnología de IntelliCode, sea mejor que el IntelliSense corriente?

Con IntelliCode, la lista de finalización sugiere la API que es probablemente más correcta para que use un desarrollador, en lugar de presentar una simple lista alfabética de los miembros. Usa el contexto de código actual del desarrollador y patrones basados en 2000 proyectos de código abierto de alta calidad en GitHub, cada uno con más de 100 estrellas, para proporcionar esta lista dinámica. Los resultados forman un modelo que predice las llamadas API más probables y más relevantes.

## P: ¿Cuál es la calidad de las sugerencias de finalización de IntelliCode?

Hemos estado usando las recomendaciones de IntelliCode de forma interna en Microsoft durante algún tiempo y creemos que las sugerencias son útiles. Aunque, en última instancia, será usted quien tenga que probar lo útiles que son estas recomendaciones mientras escribe código. Nos encantaría que le diera una oportunidad a la [extensión Visual Studio IntelliCode](https://go.microsoft.com/fwlink/?linkid=872707). Háganos saber si le sirve y envíenos sus comentarios. También entrenaremos nuestro modelo en función de lo que elija en nuestras recomendaciones y actualizaremos la extensión según mejore el modelo.

> [!NOTE]
> No se recopila ningún código definido por el usuario. Consulte la pregunta sobre [privacidad](#privacy).

## P. ¿Cuál es el futuro de IntelliCode?

Estamos estudiando una amplia variedad de formas de mejorar la productividad del desarrollador mediante IA y otras técnicas avanzadas. En Microsoft Build 2018 mostramos una primera vista de algunos de los escenarios donde creemos que la IA podría ayudar a los desarrolladores, pero hay muchas más. Estamos interesados en obtener información de los desarrolladores que experimenten con lo que hemos mostrado, así que regístrese para recibir noticias y actualizaciones en [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. ¿Cuánto cuesta?

Actualmente no disponemos de ningún anuncio sobre los precios.

## P. ¿Cuándo se lanzará IntelliCode?

IntelliSense asistido por IA de IntelliCode actualmente se encuentra en su primera versión preliminar experimental. Seguiremos actualizando la extensión experimental y agregaremos más capacidades en el futuro. No tenemos ninguna programación sobre la versión final, pero agradecemos los comentarios de los desarrolladores, para que podamos proporcionar las mejores experiencias posibles. Puede registrarse para recibir noticias y actualizaciones en [https://aka.ms/intellicode](https://aka.ms/intellicode).

## P. ¿Esta experiencia solo está disponible en Visual Studio y para C#?

La experiencia se mostró en la compilación 2018 en Visual Studio 2017, en un código de base de C#. Pero esperamos expandir IntelliCode a más idiomas y herramientas de la familia de Visual Studio en el futuro.

## P. <a name="whynointellisense"/> No veo las sugerencias de IntelliCode en mi experiencia de edición de C#. ¿Qué sucede?

Las sugerencias de IntelliCode aparecen en la experiencia estándar de IntelliSense de Visual Studio para C#. Las extensiones que reemplazan esa experiencia impiden que las sugerencias con estrella de IntelliCode aparezcan en la parte superior de la lista. Para comprobar si las extensiones están causando este comportamiento, desactívelas y vuelva a probar IntelliSense.

Si con esto no se resuelve el problema, notifíquelo mediante la característica [Notificar un problema](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-report-a-problem-with-visual-studio-2017) de Visual Studio y mencione a IntelliCode en el informe.

## P. ¿Qué versión de Visual Studio necesito para ejecutar esta extensión?

La extensión Visual Studio IntelliCode es compatible con Visual Studio 2017 versión 15.7 (versión preliminar 5) y posteriores (todas las SKU). La instalación de la extensión se detiene con el mensaje “Esta extensión no se puede instalar en ninguno de los productos instalados actualmente” si no tiene instalada la versión mínima requerida.

## P. ¿Esta experiencia solo está disponible en inglés?

IntelliCode es actualmente una extensión de versión preliminar y estamos entusiasmados por comprender lo útiles que resultan estas capacidades a un conjunto amplio de clientes. Cuando saquemos IntelliCode de la versión preliminar, por supuesto que tendremos en cuenta qué configuración regional o idioma admitiremos primero y cómo se empaquetará, en función de sus comentarios.

## <a name="privacy"/> P: ¿Qué hay de la privacidad? ¿Se enviará mi código a la nube? ¿Qué datos de clientes se envían a Microsoft?

Invitamos a los desarrolladores a probar Visual Studio IntelliCode hoy como una extensión de versión preliminar experimental. El propósito de la extensión es permitir a los desarrolladores que prueben las capacidades de IntelliCode y proporcionen comentarios al equipo del producto.

Se capturan algunos datos de uso de informe de errores anónimos de la extensión para ayudar a mejorar el producto. No se envía ningún código definido por el usuario a Microsoft, pero recopilamos información sobre el uso de los resultados de IntelliCode. Los datos solo incluyen tipos de .NET y de código abierto, y los miembros que ha seleccionado de la lista de sugerencias de IntelliCode. Los desarrolladores pueden optar por no participar en el [Programa para la mejora de la experiencia de Visual Studio](../../ide/visual-studio-experience-improvement-program.md), que también desactiva la recopilación de datos para la extensión IntelliCode. En la barra de menús, seleccione **Ayuda** > **Enviar comentarios** > **Configuración**. En el cuadro de diálogo **Programa de mejora de experiencia de Visual Studio**, seleccione **No, prefiero no participar** y, después, seleccione **Aceptar**.

La extensión de IntelliCode podría preguntar al desarrollador periódicamente para que complete una encuesta, que también es anónima. Los usuarios podrán registrarse para recibir noticias y obtener una vista previa privada futura, pero no es necesario que lo hagan actualmente para usar la extensión experimental.

Las características futuras podrían requerir acceso a un servicio, lo que requerirá que se registren. Publicaremos información más detallada cuando dichas características estén listas para la versión preliminar privada.
