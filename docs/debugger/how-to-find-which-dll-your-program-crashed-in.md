---
title: Averiguar en qué archivo DLL se ha bloqueado el programa | Microsoft Docs
description: Use la ventana Módulos para identificar qué archivo .dll externo estaba activo cuando se bloqueó la aplicación. Puede hacerlo para un archivo .dll del sistema o para el código de otra persona.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- vs.debug.dll
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6eacc8865b3f531df8651ad77d99b319278e6cd1
ms.sourcegitcommit: 620d30c60da8f9805fce524fe4951cf40f28297d
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2021
ms.locfileid: "97903395"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Procedimiento Averiguar en qué archivo DLL se ha bloqueado el programa (C#, C++, Visual Basic, F#)

 Si la aplicación se bloquea durante una llamada a un archivo DLL del sistema o el código de un tercero, es necesario que encuentre qué archivo DLL estaba activo cuando ocurrió el bloqueo. Si se produce un bloqueo de un archivo DLL fuera de su programa, puede identificar la ubicación mediante la ventana **Módulos**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para averiguar dónde se produjo un bloqueo mediante la ventana Módulos

1. Anote la dirección donde se produjo el bloqueo.

    Si la dirección no aparece en el mensaje de error, puede que necesite usar métodos alternativos para identificar el archivo DLL. Si sospecha de un archivo DLL del sistema, puede [cargar símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) desde los servidores de símbolos de Microsoft durante la depuración. De lo contrario, puede que tenga que [crear un archivo de volcado de memoria](../debugger/using-dump-files.md) con la información del montón. Hay varias [herramientas](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) para crear archivos de volcado de memoria.

2. En el menú **Depurar**, elija **Ventanas** y haga clic en **Módulos**.

3. En la ventana **Módulos**, busque la columna **Dirección**. Es posible que necesite utilizar la barra de desplazamiento para verla.

4. Haga clic en el botón **Dirección** en la parte superior de la columna para ordenar los archivos DLL por dirección.

5. Busque en la lista ordenada el archivo DLL cuyo intervalo de direcciones contiene la ubicación del bloqueo.

6. Consulte las columnas **Nombre** y **Ruta de acceso** para ver el nombre y la ruta del archivo DLL.

## <a name="see-also"></a>Vea también
- [Depurar proyectos DLL](../debugger/debugging-dll-projects.md)
- [Cómo: Uso de la ventana Módulos](../debugger/how-to-use-the-modules-window.md)