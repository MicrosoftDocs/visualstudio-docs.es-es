---
title: Actualizar Dotfuscator Community Edition (CE) | Microsoft Docs
ms.date: 2017-02-08
ms.prod: visual-studio-dev15
ms.devlang: dotnet
ms.technology:
- dotfuscator
ms.topic: article
keywords: "Dotfuscator, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2017, actualizar, línea de comandos"
helpviewer_keywords:
- PreEmptive Protection - Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator
- obfuscation
- protection
- Dotfuscator upgrade
- upgrade Dotfuscator
- upgrading Dotfuscator
- register Dotfuscator
- registering Dotfuscator
- Dotfuscator command line
- Dotfuscator Professional
description: "Obtenga información sobre cómo actualizar el producto gratuito Dotfuscator Community Edition incluido en Visual Studio 2017."
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 60ca38639f6523cdbace4efa4aa48b48d5e9a886
ms.contentlocale: es-es
ms.lasthandoff: 06/23/2017

---

# Actualizar Dotfuscator Community Edition (CE)
<a id="upgrade-dotfuscator-community-edition-ce" class="xliff"></a>

Dotfuscator Community Edition (Dotfuscator CE) ofrece muchas características de protección de aplicaciones de forma inmediata a todos los desarrolladores que usan Microsoft Visual Studio.
En cambio, hay más características disponibles para los usuarios que actualicen su versión de Dotfuscator.

## Registrar Dotfuscator CE
<a id="registering-dotfuscator-ce" class="xliff"></a>

Los usuarios registrados de Dotfuscator CE obtienen acceso a características adicionales, como [compatibilidad de línea de comandos][cli], lo que facilita la integración de Dotfuscator CE en el proceso de compilación automatizado.

El registro es rápido, sencillo y gratuito.
Para registrar Dotfuscator CE, consulte [la sección Registering Dotfuscator CE (Registrar Dotfuscator CE) en la página de introducción de la Guía de usuario completa de Dotfuscator CE][register-ce].

## Dotfuscator Professional
<a id="dotfuscator-professional" class="xliff"></a>

Mientras que Dotfuscator Community Edition proporciona un nivel básico de protección, **_PreEmptive Protection - Dotfuscator_ Professional Edition** incluye transformaciones de ofuscación y capacidades de protección mejoradas.
Se incluyen los siguientes:

* *Protección de la propiedad intelectual*
  * Opciones adicionales de cambio de nombre, incluidos Enhanced Overload Induction™ y la selección aleatoria de un identificador.
  * Herramientas para descodificar seguimientos de la pila ofuscados.
  * Acceso a las transformaciones de ofuscación de nivel empresarial, incluidas las [transformaciones destinadas a anular la descompilación de código automatizada][control-flow].
  * La capacidad de [ocultar cadenas confidenciales][string-encryption], lo que hace imposible que se realice una búsqueda sencilla del código descompilado.
  * La capacidad de [insertar discretamente cadenas de propiedad y distribución en los ensamblados][watermarking] (marca de agua de software), lo que le permite determinar el origen de pérdidas de software no autorizadas.
  * La capacidad de [combinar varios ensamblados en uno][linking], lo que dificulta aún más que los atacantes determinen los roles de elementos de código, ya que se ha eliminado la separación de preocupaciones.
  * La capacidad de [quitar de forma automática el código que no se usa de la aplicación][pruning], lo que reduce la cantidad de código confidencial que se distribuye.
* *Protección de la integridad de la aplicación*
  * [Comportamientos adicionales de defensa de la aplicación][check-actions].
  * La capacidad de insertar código contra alteraciones y depuraciones en ensamblados `.dll`.
  * La capacidad de proporcionar un período de advertencia antes de la fecha límite de fin de ciclo de vida de la aplicación.
  * La capacidad de notificar el código de aplicación durante un período de advertencia de fin de ciclo de vida o después de la fecha límite.
  * Cifrado de telemetría.
* *Supervisión de aplicaciones*
  * La capacidad de recopilar y guardar la información recopilada durante interrupciones de red temporales.
  * La capacidad de recopilar información de identificación personal.
  * Uso ilimitado del [seguimiento de características][features].
  * La capacidad de realizar un seguimiento de las excepciones detectadas y producidas por el código, además de las excepciones no controladas.
  * La capacidad de realizar un seguimiento de las excepciones en ensamblados `.dll`.
  * Cifrado de telemetría.

Dotfuscator Professional es el [.NET Obfuscator][net-obfuscator] estándar del sector y es adecuado para los desarrolladores empresariales que necesitan actualizaciones de producto, mantenimiento y soporte de forma continua.
Además, Dotfuscator Professional ofrece una mayor integración con Visual Studio y tiene licencia para uso comercial.

Para obtener más información sobre las características avanzadas de protección de aplicaciones que ofrece Dotfuscator Professional, visite la [página de información general de Dotfuscator][product-about] de PreEmptive Solutions y [compárelo con Community Edition][product-compare].
[En preemptive.com puede solicitar versiones de evaluación totalmente compatibles][eval].

## Vea también
<a id="see-also" class="xliff"></a>

[Este tema en la guía de usuario completa de Dotfuscator CE][full]

<!-- Copyright © 2017 PreEmptive Solutions, LLC -->

[control-flow]: https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]: https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]: https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]: https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]: https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Check%20Actions.html
[features]: https://www.preemptive.com/images/stories/Dotfuscator/webframe.html#Feature_Usage_Tracking_and_the_Feature_Attribute.html

[net-obfuscator]: https://www.preemptive.com/products/dotfuscator/overview
[eval]: https://www.preemptive.com/eval-request

[product-about]: https://www.preemptive.com/products/dotfuscator/overview
[product-compare]: https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]: https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]: https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html

