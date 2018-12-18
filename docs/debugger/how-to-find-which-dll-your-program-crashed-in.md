---
title: 'Cómo: buscar el archivo DLL que se bloqueó en el programa | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
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
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 40f27e0bec20e1dd037beaa5f60ea648c0ccb171
ms.sourcegitcommit: a7de99f36e9ead7ea9e9bac23c88d05ddfc38b00
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52257102"
---
# <a name="how-to-find-which-dll-your-program-crashed-in-c-c-visual-basic-f"></a>Cómo: buscar el archivo DLL que se bloqueó en el programa (C#, C++, Visual Basic, F#)
  
 Si la aplicación se bloquea durante una llamada a un archivo DLL del sistema o el código de un tercero, es necesario que encuentre qué archivo DLL estaba activo cuando ocurrió el bloqueo. Si experimenta un bloqueo en un archivo DLL fuera de su propio programa, puede identificar la ubicación mediante el **módulos** ventana.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para averiguar dónde se produjo un bloqueo mediante la ventana Módulos  
  
1.  Anote la dirección donde se produjo el bloqueo.

    Si la dirección no se muestra en el mensaje de error, deberá usar los métodos alternativos para identificar el archivo DLL. Si sospecha que una DLL del sistema, también puede [cargar símbolos](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md) desde los servidores de símbolos de Microsoft cuando se depura. En caso contrario, es posible que deba [crear un archivo de volcado](../debugger/using-dump-files.md) con el montón información en su lugar. Diversos [herramientas](https://blogs.msdn.microsoft.com/andrehal/2009/12/31/what-is-a-dump-and-how-do-i-create-one/) están disponibles para crear archivos de volcado.
  
2.  En el **depurar** menú, elija **Windows**y haga clic en **módulos**.  
  
3.  En el **módulos** ventana, busque la **dirección** columna. Es posible que necesite utilizar la barra de desplazamiento para verla.  
  
4.  Haga clic en el **dirección** situado en la parte superior de la columna para ordenar los archivos DLL por dirección.  
  
5.  Busque en la lista ordenada el archivo DLL cuyo intervalo de direcciones contiene la ubicación del bloqueo.  
  
6.  Examine el **nombre** y **ruta** columnas para ver el nombre del archivo DLL y la ruta de acceso.  
  
## <a name="see-also"></a>Vea también  
 [Depurar proyectos DLL](../debugger/debugging-dll-projects.md)   
 [Cómo: Usar la ventana Módulos](../debugger/how-to-use-the-modules-window.md)