---
title: Procedimiento Busque el archivo DLL que se bloqueó en el programa | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
f1_keywords:
- vs.debug.dll
dev_langs:
- FSharp
- VB
- CSharp
- C++
- VB
- CSharp
- C++
helpviewer_keywords:
- debugger, DLL crashes
- Module List dialog box
- errors [debugger], DLL crashes
- Modules window
- debugging [Visual Studio], DLL crashes
- DLLs, load order of
ms.assetid: ecf62568-8b65-4a41-b8a4-e962ff2dfb71
caps.latest.revision: 22
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1da5ba504c22f78ebd3c0705bd5ee903fb4a2997
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60060571"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Procedimiento Busque el archivo DLL que se bloqueó en el programa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si la aplicación se bloquea durante una llamada a un archivo DLL del sistema o el código de un tercero, es necesario que encuentre qué archivo DLL estaba activo cuando ocurrió el bloqueo. Si se produce un bloqueo de un archivo DLL fuera de su programa, puede identificar la ubicación mediante la ventana **Módulos**.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para averiguar dónde se produjo un bloqueo mediante la ventana Módulos  
  
1. Anote la dirección donde se produjo el bloqueo.  
  
2. En el menú **Depurar**, elija **Ventanas** y haga clic en **Módulos**.  
  
3. En la ventana **Módulos**, busque la columna **Dirección**. Es posible que necesite utilizar la barra de desplazamiento para verla.  
  
4. Haga clic en el botón **Dirección** en la parte superior de la columna para ordenar los archivos DLL por dirección.  
  
5. Busque en la lista ordenada el archivo DLL cuyo intervalo de direcciones contiene la ubicación del bloqueo.  
  
6. Consulte las columnas **Nombre** y **Ruta de acceso** para ver el nombre y la ruta del archivo DLL.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Depurar archivos DLL nativos](../debugger/how-to-debug-native-dlls.md)   
 [Cómo: Uso de la ventana Módulos](../debugger/how-to-use-the-modules-window.md)
