---
title: Inspección de una excepción
titleSuffix: ''
ms.date: 1/18/2020
ms.topic: how-to
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JavaScript
helpviewer_keywords:
- exception helper, debugger, exception
- debugging [Visual Studio], exception helper, Examine an exception
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d0084abff760ff227b20137cd55d905b57e1a18
ms.sourcegitcommit: 062615c058d2ff44751e8d0c704ccfa3c5543469
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/22/2020
ms.locfileid: "90852503"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Inspeccionar una excepción mediante la Aplicación auxiliar de excepciones 

Tratar con excepciones es un problema común, independientemente de su tecnología o nivel de conocimientos. Puede ser una experiencia frustrante descubrir por qué las excepciones están causando problemas en el código. Al depurar una excepción en Visual Studio, queremos reducir esa frustración proporcionándole información de excepción pertinente para ayudarle a depurar el problema con más rapidez.

![Asistente de excepciones](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Pausa en la excepción
Cuando el depurador se interrumpe en una excepción, aparece un icono de error de excepción a la derecha de la línea de código. Aparecerá una Aplicación auxiliar de excepciones no modal cerca del icono de excepción.

![Aplicación auxiliar de excepciones junto a una línea de código](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Inspección de la información de la excepción
Puede leer de forma instantánea el tipo de excepción y el mensaje de excepción en la Aplicación auxiliar de excepciones, y si la excepción se inició o no se controló. Puede inspeccionar y ver las propiedades del objeto de excepción haciendo clic en el vínculo **Ver detalles**.

## <a name="analyze-null-references"></a>Análisis de referencias nulas
A partir de Visual Studio 2017, para el código de .Net y C/C++, cuando se alcanza un `NullReferenceException` o un `AccessViolation`, se ve información de análisis nula en la Aplicación auxiliar de excepciones. El análisis se muestra como texto debajo del mensaje de excepción. En la ilustración siguiente, la información se muestra como "**s** era null.".

![Análisis de valores nulos de la Aplicación auxiliar de excepciones](media/debugger-exception-helper-default.png)


> [!NOTE]
> El análisis de referencias nulas en código administrado requiere la versión 4.6.2 de .NET. Actualmente no se admite el análisis de valores NULL para Plataforma universal de Windows (UWP) y cualquier otra aplicación de .NET Core. Solo está disponible durante la depuración de código que no tiene ninguna optimización de código Just-in-Time (JIT).

## <a name="configure-exception-settings"></a>Definición de la configuración de excepciones 
Puede configurar el depurador para que se interrumpa cuando se inicie una excepción del tipo actual desde la sección **Configuración de excepciones** de la Aplicación auxiliar de excepciones. Si el depurador está en pausa en una excepción iniciada, puede usar la casilla para deshabilitar la interrupción en ese tipo de excepción cuando se inicie en el futuro. Si no desea realizar la interrupción en esta excepción particular cuando se inicia en este módulo concreto, marque la casilla por el nombre del módulo en **Excepto si se produce en:** en la ventana **Configuración de excepciones**. 

## <a name="inspect-inner-exceptions"></a>Inspección de excepciones internas 
Si la excepción tiene excepciones internas ([InnerException](/dotnet/api/system.exception.innerexception)), puede verlas en la Aplicación auxiliar de excepciones. Si hay varias excepciones presentes, puede desplazarse entre ellas mediante las flechas izquierda y derecha que se muestran encima de la pila de llamadas.

![Aplicación auxiliar de excepciones con excepción interna](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Inspección de excepciones reiniciadas
En los casos en los que el estado de una excepción es `thrown`, la Aplicación auxiliar de excepciones muestra la pila de llamadas desde la primera vez que se inició la excepción. Si la excepción se inició varias veces, solo se muestra la pila de llamadas desde la excepción original.

![Aplicación auxiliar de excepciones con excepciones reiniciadas](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Uso compartido de una sesión de depuración con Live Share
En la Aplicación auxiliar de excepciones, puede iniciar una sesión de [Live Share](/visualstudio/liveshare/) mediante el vínculo **Iniciar sesión de Live Share...** . Cualquiera que se una a la sesión de Live Share puede ver la Aplicación auxiliar de excepciones junto con cualquier otra información de depuración.