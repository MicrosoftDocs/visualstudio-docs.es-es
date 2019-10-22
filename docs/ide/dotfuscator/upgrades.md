---
title: Actualización de Dotfuscator Community
ms.date: 03/28/2019
ms.devlang: dotnet
ms.topic: conceptual
keywords: Dotfuscator, Dotfuscator Community, Dotfuscator CE, PreEmptive, PreEmptive Solutions, PreEmptive Protection, protección, community edition, ofuscación, .NET, gratuito, Visual Studio 2019, Visual Studio 2017, Visual Studio, actualización, línea de comandos
helpviewer_keywords:
- PreEmptive Protection Dotfuscator
- Dotfuscator Community Edition
- Dotfuscator CE
- Dotfuscator Community
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
description: Aprenda a actualizar la copia gratuita de Dotfuscator Community incluida en Visual Studio.
ms.assetid: c7c60904-27f9-4f1f-b79b-ddf65041b810
author: Joe-Sewell-PreEmptive
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: cee876a3904d5c47b43b58793087c901e8444dd3
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62557247"
---
# <a name="upgrade-dotfuscator-community"></a>Actualización de Dotfuscator Community

Dotfuscator Community ofrece muchas características de protección de aplicaciones de forma inmediata a todos los desarrolladores que usan Microsoft Visual Studio.
En cambio, hay más características disponibles para los usuarios que actualicen su versión de Dotfuscator.

## <a name="registering-dotfuscator-community"></a>Registro de Dotfuscator Community

Los usuarios registrados de Dotfuscator Community obtienen acceso a características adicionales, como [compatibilidad de línea de comandos][cli], lo que facilita la integración de Dotfuscator Community en el proceso de compilación automatizado. Además, el registro le concede acceso a una herramienta integrada empleada para [descodificar seguimientos de la pila ofuscados][decode-obfuscated].

El registro es rápido, sencillo y gratuito.
Para registrar Dotfuscator Community, consulte [las instrucciones que aparecen en la guía de usuario completa de Dotfuscator Community][register-ce].

## <a name="dotfuscator-professional"></a>Dotfuscator Professional

Mientras que Dotfuscator Community proporciona un nivel básico de protección, ***PreEmptive Protection - Dotfuscator Professional Edition*** incluye transformaciones de ofuscación y funcionalidades de protección mejoradas, como:

* *Protección de la propiedad intelectual*
  * Opciones adicionales de cambio de nombre, incluidos Enhanced Overload Induction™ y la selección aleatoria de un identificador.
  * Acceso a las transformaciones de ofuscación de nivel empresarial, incluidas las [transformaciones destinadas a anular la descompilación de código automatizada][control-flow].
  * La capacidad de [ocultar cadenas confidenciales][string-encryption], lo que hace imposible que se realice una búsqueda sencilla del código descompilado.
  * La capacidad de [insertar discretamente cadenas de propiedad y distribución en los ensamblados][watermarking], lo que le permite determinar el origen de pérdidas de software no autorizadas.
  * La capacidad de [combinar varios ensamblados en uno][linking], lo que dificulta aún más que los atacantes determinen los roles de elementos de código, ya que se ha eliminado la separación de preocupaciones.
  * La capacidad de [quitar de forma automática el código que no se usa de la aplicación][pruning], lo que reduce la cantidad de código confidencial que se distribuye.
* *Protección de la integridad de la aplicación*
  * [Comportamientos adicionales de defensa de la aplicación][check-actions].
  * La capacidad de proporcionar un período de advertencia antes de la fecha límite de fin de ciclo de vida de la aplicación.
  * La capacidad de notificar el código de aplicación durante un período de advertencia de fin de ciclo de vida o después de la fecha límite.

Dotfuscator Professional es el [.NET Obfuscator][net-obfuscator] estándar del sector y es adecuado para los desarrolladores empresariales que necesitan actualizaciones de producto, mantenimiento y soporte de forma continua.
Además, Dotfuscator Professional ofrece una mayor integración con Visual Studio y tiene licencia para uso comercial.

Para obtener más información sobre las características avanzadas de protección de aplicaciones que ofrece Dotfuscator Professional, visite la [página de información general de Dotfuscator][product-about] de PreEmptive Solutions y [compárelo con Community Edition][product-compare].
[En preemptive.com hay versiones de evaluación totalmente compatibles][eval].

## <a name="see-also"></a>Vea también

[Este artículo en la guía de usuario completa de Dotfuscator Community][full]

<!-- Copyright © 2019 PreEmptive Solutions, LLC -->

[control-flow]:  https://www.preemptive.com/products/dotfuscator/features#controlflow
[string-encryption]:  https://www.preemptive.com/products/dotfuscator/features#string
[watermarking]:  https://www.preemptive.com/products/dotfuscator/features#watermarking
[linking]:  https://www.preemptive.com/products/dotfuscator/features#linking
[pruning]:  https://www.preemptive.com/products/dotfuscator/features#pruning

[check-actions]:  https://www.preemptive.com/dotfuscator/pro/userguide/en/protection_checks_overview.html#actions

[net-obfuscator]:  https://www.preemptive.com/products/dotfuscator/overview
[eval]:  https://www.preemptive.com/eval-request

[product-about]:  https://www.preemptive.com/products/dotfuscator/overview
[product-compare]:  https://www.preemptive.com/products/dotfuscator/compare-editions

[cli]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_cli.html
[register-ce]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_getstarted.html#register

[full]:  https://www.preemptive.com/dotfuscator/ce/docs/help/intro_upgrades.html
[decode-obfuscated]:  https://www.preemptive.com/dotfuscator/ce/docs/help/gui_decode_stack_trace.html