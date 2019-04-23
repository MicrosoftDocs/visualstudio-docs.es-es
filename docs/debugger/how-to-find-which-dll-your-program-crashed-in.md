---
title: Procedimiento Busque el archivo DLL que se bloqueó en el programa | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b7a9421af9e0caf085feb1afb27b53befe837668
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60072583"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Procedimiento Busque el archivo DLL que se bloqueó en el programa (C#, C++, Visual Basic, F#)

 Si la aplicación se bloquea durante una llamada a un archivo DLL del sistema o el código de un tercero, es necesario que encuentre qué archivo DLL estaba activo cuando ocurrió el bloqueo. Si se produce un bloqueo de un archivo DLL fuera de su programa, puede identificar la ubicación mediante la ventana **Módulos**.

### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para averiguar dónde se produjo un bloqueo mediante la ventana Módulos

1. Anote la dirección donde se produjo el bloqueo.

    Si la dirección no se muestra en el mensaje de error, deberá usar los métodos alternativos para identificar el archivo DLL. Si sospecha que una DLL del sistema, también puede [cargar símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) desde los servidores de símbolos de Microsoft cuando se depura. En caso contrario, es posible que deba [crear un archivo de volcado](../debugger/using-dump-files.md) con el montón información en su lugar. Diversos [herramientas](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) están disponibles para crear archivos de volcado.

2. En el menú **Depurar**, elija **Ventanas** y haga clic en **Módulos**.

3. En la ventana **Módulos**, busque la columna **Dirección**. Es posible que necesite utilizar la barra de desplazamiento para verla.

4. Haga clic en el botón **Dirección** en la parte superior de la columna para ordenar los archivos DLL por dirección.

5. Busque en la lista ordenada el archivo DLL cuyo intervalo de direcciones contiene la ubicación del bloqueo.

6. Consulte las columnas **Nombre** y **Ruta de acceso** para ver el nombre y la ruta del archivo DLL.

## <a name="see-also"></a>Vea también
- [Depurar proyectos DLL](../debugger/debugging-dll-projects.md)
- [Cómo: Uso de la ventana Módulos](../debugger/how-to-use-the-modules-window.md)