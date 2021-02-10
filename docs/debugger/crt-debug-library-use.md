---
title: Uso de la biblioteca de depuración CRT | Microsoft Docs
description: Obtenga información sobre cómo la biblioteca en tiempo de ejecución de C (CRT) es compatible con los esfuerzos de depuración y qué debe hacer para usar las bibliotecas de depuración de CRT.
ms.custom: SEO-VS-2020
ms.date: 10/03/2019
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- /DEBUG linker option [C++]
- crtdbg.h file
- debug library
- MDd compiler option [C++]
- libraries, CRT debug library
- MTd compiler option [C++]
- LDd compiler function [C++]
- /MTd compiler option [C++]
- /MDd compiler option [C++]
- debugging [CRT], CRT debug library
- DEBUG linker option [C++]
- /LDd compiler function [C++]
ms.assetid: 464de16b-4215-4787-9bfa-921aaff9d9f4
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: fe50082f8ff62c4a19b7725facc18f43d672e353
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/08/2021
ms.locfileid: "99865714"
---
# <a name="crt-debug-library-use"></a>Uso de la biblioteca de depuración CRT
La biblioteca en tiempo de ejecución de C (CRT) proporciona amplias capacidades de depuración. Si quiere usar una de las bibliotecas de depuración de CRT, debe crear un vínculo con [/DEBUG](/cpp/build/reference/debug-generate-debug-info) y compilar con **/MDd**, **/MTd** o **/LDd**.

## <a name="remarks"></a>Comentarios
 Las principales definiciones y macros para la depuración con CRT se encuentran en el archivo de encabezado CRTDBG.h.

 Las funciones de las bibliotecas de depuración CRT se compilan con información de depuración ([/Z7, /Zd, /Zi, /ZI (Formato de información de depuración)](/cpp/build/reference/z7-zi-zi-debug-information-format)) y sin optimización. Algunas funciones contienen aserciones para comprobar los parámetros que se les pasan; además, se proporciona el código fuente. Con este código fuente, se pueden ejecutar las funciones CRT paso a paso para confirmar si las funciones se comportan como se esperaba y para comprobar si existen parámetros o estados de memoria incorrectos. Parte de la tecnología de CRT es propietaria y no proporciona el código fuente para el tratamiento de excepciones, punto flotante y algunas otras rutinas.

 Para obtener más información sobre las diversas bibliotecas en tiempo de ejecución que se pueden utilizar, vea [Bibliotecas en tiempo de ejecución de C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Vea también

- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](/cpp/build/reference/md-mt-ld-use-run-time-library)