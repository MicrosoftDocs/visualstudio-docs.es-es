---
title: Uso de la biblioteca de depuración de CRT | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- c.debug.runtime
dev_langs:
- FSharp
- VB
- CSharp
- C++
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
caps.latest.revision: 19
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 51534d226f3ae0f8726bb818423bf0a9b788fd8c
ms.sourcegitcommit: c496a77add807ba4a29ee6a424b44a5de89025ea
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/24/2019
ms.locfileid: "58988161"
---
# <a name="crt-debug-library-use"></a>Uso de la biblioteca de depuración CRT
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La biblioteca en tiempo de ejecución de C (CRT) proporciona amplias capacidades de depuración. Para usar una de las bibliotecas de depuración de CRT, debe vincular con [/DEBUG](http://msdn.microsoft.com/library/1af389ae-3f8b-4d76-a087-1cdf861e9103) y compile con **/MDd**, **/MTd**, o **/LDd**.  
  
## <a name="remarks"></a>Comentarios  
 Las principales definiciones y macros para la depuración con CRT se encuentran en el archivo de encabezado CRTDBG.h.  
  
 Las funciones de las bibliotecas de depuración CRT se compilan con información de depuración ([/Z7, /Zd, /Zi, /ZI (Formato de información de depuración)](http://msdn.microsoft.com/library/ce9fa7e1-0c9b-47e3-98ea-26d1a16257c8)) y sin optimización. Algunas funciones contienen aserciones para comprobar los parámetros que se les pasan; además, se proporciona el código fuente. Con este código fuente, se pueden ejecutar las funciones CRT paso a paso para confirmar si las funciones se comportan como se esperaba y para comprobar si existen parámetros o estados de memoria incorrectos. Parte de la tecnología de CRT es propietaria y no proporciona el código fuente para el tratamiento de excepciones, punto flotante y algunas otras rutinas.  
  
 Cuando se instala Visual C++, existe la opción de instalar el código fuente de la biblioteca en tiempo de ejecución de C en el disco duro. Si no se instala, se necesitará el CD-ROM para ejecutar las funciones de CRT paso a paso.  
  
 Para obtener más información sobre las diversas bibliotecas en tiempo de ejecución que se pueden utilizar, vea [Bibliotecas en tiempo de ejecución de C](http://msdn.microsoft.com/library/a889fd39-807d-48f2-807f-81492612463f).  
  
## <a name="see-also"></a>Vea también  
 [Técnicas de depuración de CRT](../debugger/crt-debugging-techniques.md)   
 [/MD, /MT, /LD (Usar la biblioteca en tiempo de ejecución)](http://msdn.microsoft.com/library/cf7ed652-dc3a-49b3-aab9-ad60e5395579)
