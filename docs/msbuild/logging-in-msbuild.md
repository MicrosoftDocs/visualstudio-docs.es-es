---
title: Registro de MSBuild | Microsoft Docs
description: Obtenga información sobre cómo el registro de MSBuild proporciona una manera de supervisar el progreso de la compilación mediante la captura de eventos de compilación, mensajes, advertencias y errores en un archivo de registro.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- msbuild, logging
ms.assetid: 9aea2e76-8f60-4234-913d-598e7bbad808
author: ghogen
ms.author: ghogen
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: afbb79e2ce8ebdccc68def6ca4c42fde85c11bf0
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99966258"
---
# <a name="logging-in-msbuild"></a>Registro de MSBuild

El registro proporciona una manera de supervisar el progreso de una compilación. El registro captura los eventos, los mensajes, las advertencias y los errores de compilación en un archivo de registro.

## <a name="in-this-section"></a>En esta sección

- [Obtener registros de compilación](../msbuild/obtaining-build-logs-with-msbuild.md)

 Describe los diferentes aspectos del registro de MSBuild.

- [Registradores de compilación](../msbuild/build-loggers.md)

 Describe los pasos necesarios para crear un registrador de procesador único.

- [Registrar en un entorno de varios procesadores](../msbuild/logging-in-a-multi-processor-environment.md)

 Describe cómo funciona el registro en un entorno de varios procesadores y los dos modelos de registro para varios procesadores.

- [Escribir registradores que reconocen varios procesadores](../msbuild/writing-multi-processor-aware-loggers.md)

 Describe cómo crear registradores que reconocen varios procesadores y cómo utilizar ConfigurableForwardingLogger.

- [Crear registradores de reenvío](../msbuild/creating-forwarding-loggers.md)

 Describe cómo crear registradores de reenvío personalizados.

## <a name="see-also"></a>Consulte también

- [Compilar varios proyectos en paralelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md) Describe cómo compilar varios proyectos más rápidamente al ejecutarlos en paralelo.
