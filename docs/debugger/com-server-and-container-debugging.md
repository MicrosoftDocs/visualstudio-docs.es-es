---
title: Servidor COM y un contenedor de depuración | Documentos de Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.debug.com
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- ActiveX control container debugging [Visual Studio]
- debugging ActiveX controls
- COM servers, debugging
- ActiveX controls, debugging
- COM [Visual Studio], debugging
ms.assetid: b7ce8696-ebb8-4354-a767-f76b8ada4ac1
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 40edce29e8d40310f6eab37309c4c2ca7eb8a85a
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62564000"
---
# <a name="com-server-and-container-debugging"></a>Depuración de servidores y contenedores COM
Las aplicaciones COM realizan una serie de tareas fuera del control directo del programador. La comunicación entre archivos DLL, los contadores de uso en objetos y las operaciones del Portapapeles son sólo algunas de las áreas en las que se puede encontrar un comportamiento inesperado. Cuando esto ocurre, el primer paso es determinar el origen del problema.

 El depurador de Visual Studio permite la depuración superficial o exhaustiva de contenedores y servidores. Esto incluye la capacidad de ejecutar instrucciones paso a paso entre llamadas a procedimientos remotos (RPC).

## <a name="BKMK_COMServerandContainerintheSameSolution"></a> Depuración de un servidor COM y un contenedor en la misma solución
 Se puede depurar un servidor y contenedor COM mediante dos proyectos dentro de la misma solución. Establezca los puntos de interrupción apropiados en cada proyecto y depure. Cuando el contenedor llama al servidor que visita un punto de interrupción, el contenedor esperará hasta que regrese el código del servidor, es decir, hasta que termine de depurarlo.

 La depuración de un contenedor COM es similar a la de un programa estándar. Una diferencia está en la depuración de un evento que genera una devolución de llamada (por ejemplo, al arrastrar datos a la aplicación contenedora). En este caso, debe establecer un punto de interrupción en la función de devolución de llamada.

## <a name="BKMK_ServerApplicationWithoutContainerInformation"></a> Depuración de una aplicación de servidor sin información del contenedor
 Si no tiene o no desea utilizar información de depuración para la aplicación contenedora, puede empezar el proceso de depuración de la aplicación del servidor en tres pasos:

1. Comience a depurar el servidor como si se tratara de una aplicación normal.

2. Establezca puntos de interrupción donde desee.

3. Inicie la aplicación contenedora.

## <a name="BKMK_DebuggingaServerandDomainIsolationSDIApplication"></a> Depuración de una aplicación de Aislamiento de servidor y dominio (SDI)
 Si está depurando una aplicación de servidor SDI, debe especificar `/Embedding` o `/Automation` en la propiedad **Argumentos de la línea de comandos** del cuadro de diálogo Páginas de propiedades de *proyecto* de los proyectos de C/C++, C# o Visual Basic.

 Con los argumentos de esta línea de comandos, el depurador puede iniciar la aplicación de servidor como si se iniciara desde un contenedor. Después, al iniciar el contenedor desde el Administrador de programas o desde el Administrador de archivos, el contenedor utilizará la instancia del servidor que se inició en el depurador.

 Para tener acceso al cuadro de diálogo Páginas de propiedades de *proyecto*, haga clic con el botón derecho en el proyecto desde el Explorador de soluciones y después elija Propiedades en el menú contextual. Para buscar la propiedad Argumentos de la línea de comandos, haga clic en la ficha Depurar y vaya a Opciones de inicio.

## <a name="see-also"></a>Vea también

- [Depurar COM y ActiveX](../debugger/com-and-activex-debugging.md)