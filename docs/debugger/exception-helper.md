---
title: 'Inspeccionar una excepción: Visual Studio | Microsoft Docs'
ms.date: 1/18/2020
ms.topic: conceptual
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
ms.openlocfilehash: 2dae1609486ec4f3462be89b0526467dd7414647
ms.sourcegitcommit: 8cbced0fb46959a3a2494852df1e41db1177a26c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2020
ms.locfileid: "76829760"
---
# <a name="inspect-an-exception-using-the-exception-helper"></a>Inspeccionar una excepción mediante la aplicación auxiliar de excepciones 

Tratar con excepciones es un problema común, independientemente de su tecnología o nivel de conocimientos. Puede ser una experiencia frustrante que averigüe por qué las excepciones están causando problemas en el código. Al depurar una excepción en Visual Studio, queremos reducir esa frustración proporcionándole información de excepción importante para ayudarle a depurar el problema con más rapidez.

![Asistente de excepciones](media/debugger-exception-helper-default.png)

## <a name="pause-on-the-exception"></a>Pausar en la excepción
Cuando el depurador se interrumpe en una excepción, aparece un icono de error de excepción a la derecha de la línea de código. Aparecerá una aplicación auxiliar de excepción no modal cerca del icono de excepción.

![Aplicación auxiliar de excepciones junto a una línea de código](media/debugger-exception-helper-locerror.png)

## <a name="inspect-exception-info"></a>Inspeccionar la información de la excepción
Puede leer de forma instantánea el tipo de excepción y el mensaje de excepción en la aplicación auxiliar de excepciones, y si la excepción se inició o no. Puede inspeccionar y ver las propiedades del objeto de excepción haciendo clic en el vínculo **Ver detalles** .

## <a name="analyze-null-references"></a>Analizar referencias nulas
A partir de Visual Studio 2017, para .net y C/C++ Code, cuando se alcanza un `NullReferenceException` o un `AccessViolation`, se ve información de análisis null en la aplicación auxiliar de excepciones. El análisis se muestra como texto debajo del mensaje de excepción. En la ilustración siguiente, la información se muestra como "**s** era null.".

![Análisis de valores NULL de la aplicación auxiliar de excepciones](media/debugger-exception-helper-default.png)


> [!NOTE]
> El análisis de referencia null en código administrado requiere la versión 4.6.2 de .NET. Actualmente no se admite el análisis de valores NULL para Plataforma universal de Windows (UWP) y cualquier otra aplicación de .NET Core. Solo está disponible durante la depuración de código que no tiene ninguna optimización de código Just-in-Time (JIT).

## <a name="configure-exception-settings"></a>Configurar las opciones de excepción 
Puede configurar el depurador para que se interrumpa cuando se produzca una excepción del tipo actual desde la sección de **configuración de excepciones** de la aplicación auxiliar de excepciones. Si el depurador está en pausa en una excepción iniciada, puede usar la casilla para deshabilitar la interrupción en ese tipo de excepción cuando se inicie en el futuro. Si no desea interrumpir esta excepción determinada cuando se produce en este módulo concreto, marque la casilla por el nombre del módulo en **excepto si se produce desde:** en la ventana **configuración de excepciones** . 

## <a name="inspect-inner-exceptions"></a>Inspeccionar excepciones internas 
Si la excepción tiene excepciones internas ([InnerException](https://docs.microsoft.com/dotnet/api/system.exception.innerexception), puede verlas en la aplicación auxiliar de excepciones. Si hay varias excepciones presentes, puede desplazarse entre ellas mediante las flechas izquierda y derecha que se muestran encima de la pila de llamadas.

![Aplicación auxiliar de excepciones con excepción interna](media/debugger-exception-helper-innerexception.png)

## <a name="inspect-rethrown-exceptions"></a>Inspeccionar excepciones de reinicio
En los casos en los que se ha `thrown` una excepción, la aplicación auxiliar de excepciones muestra la pila de llamadas desde la primera vez que se produjo la excepción. Si la excepción se produjo varias veces, solo se muestra la pila de llamadas de la excepción original.

![Aplicación auxiliar de excepciones con excepciones rethrowon](media/debugger-exception-helper-innerexception.png)

## <a name="share-a-debug-session-with-live-share"></a>Compartir una sesión de depuración con Live Share
Desde la aplicación auxiliar de excepciones, puede iniciar una sesión de [Live share](https://docs.microsoft.com/visualstudio/liveshare/) mediante el vínculo **iniciar sesión Live share..** .. Cualquier persona que se una a la sesión Live Share puede ver la aplicación auxiliar de excepciones junto con cualquier otra información de depuración.
