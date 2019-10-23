---
title: Uso de la biblioteca de depuración de CRT | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 20aeee220bec600c2232286d18600b04201ad03b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/22/2019
ms.locfileid: "72745606"
---
# <a name="crt-debug-library-use"></a>Uso de la biblioteca de depuración CRT
La biblioteca en tiempo de ejecución de C (CRT) proporciona amplias capacidades de depuración. Para utilizar una de las bibliotecas de depuración de CRT, debe vincular con [/Debug](/cpp/build/reference/debug-generate-debug-info) y compilar con **/mdd**, **/MTD**o **/LDd**.

## <a name="remarks"></a>Comentarios
 Las principales definiciones y macros para la depuración con CRT se encuentran en el archivo de encabezado CRTDBG.h.

 Las funciones de las bibliotecas de depuración CRT se compilan con información de depuración ([/Z7, /Zd, /Zi, /ZI (Formato de información de depuración)](/cpp/build/reference/z7-zi-zi-debug-information-format)) y sin optimización. Algunas funciones contienen aserciones para comprobar los parámetros que se les pasan; además, se proporciona el código fuente. Con este código fuente, se pueden ejecutar las funciones CRT paso a paso para confirmar si las funciones se comportan como se esperaba y para comprobar si existen parámetros o estados de memoria incorrectos. Parte de la tecnología de CRT es propietaria y no proporciona el código fuente para el tratamiento de excepciones, punto flotante y algunas otras rutinas.

 Para obtener más información sobre las diversas bibliotecas en tiempo de ejecución que se pueden utilizar, vea [Bibliotecas en tiempo de ejecución de C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Vea también

- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](/cpp/build/reference/md-mt-ld-use-run-time-library)