---
title: Uso de la biblioteca de depuración de CRT | Documentos de Microsoft
ms.date: 11/04/2016
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
ms.openlocfilehash: 9434be46f357a97ad01f10ceec184ebe6c52eb43
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62565552"
---
# <a name="crt-debug-library-use"></a>Uso de la biblioteca de depuración CRT
La biblioteca en tiempo de ejecución de C (CRT) proporciona amplias capacidades de depuración. Para usar una de las bibliotecas de depuración de CRT, debe vincular con [/DEBUG](/cpp/build/reference/debug-generate-debug-info) y compile con **/MDd**, **/MTd**, o **/LDd**.

## <a name="remarks"></a>Comentarios
 Las principales definiciones y macros para la depuración con CRT se encuentran en el archivo de encabezado CRTDBG.h.

 Las funciones de las bibliotecas de depuración CRT se compilan con información de depuración ([/Z7, /Zd, /Zi, /ZI (Formato de información de depuración)](/cpp/build/reference/z7-zi-zi-debug-information-format)) y sin optimización. Algunas funciones contienen aserciones para comprobar los parámetros que se les pasan; además, se proporciona el código fuente. Con este código fuente, se pueden ejecutar las funciones CRT paso a paso para confirmar si las funciones se comportan como se esperaba y para comprobar si existen parámetros o estados de memoria incorrectos. Parte de la tecnología de CRT es propietaria y no proporciona el código fuente para el tratamiento de excepciones, punto flotante y algunas otras rutinas.

 Cuando se instala Visual C++, existe la opción de instalar el código fuente de la biblioteca en tiempo de ejecución de C en el disco duro. Si no se instala, se necesitará el CD-ROM para ejecutar las funciones de CRT paso a paso.

 Para obtener más información sobre las diversas bibliotecas en tiempo de ejecución que se pueden utilizar, vea [Bibliotecas en tiempo de ejecución de C](/cpp/c-runtime-library/crt-library-features).

## <a name="see-also"></a>Vea también

- [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)
- [/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](/cpp/build/reference/md-mt-ld-use-run-time-library)