---
title: 'Cómo: buscar el archivo DLL que se bloqueó en el programa | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
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
manager: ghogen
ms.openlocfilehash: b7af6940de5bd4e39451f44176f5c15d2e8b4548
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51778402"
---
# <a name="how-to-find-which-dll-your-program-crashed-in"></a>Cómo: Averiguar en qué archivo DLL se bloqueó el programa
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

NOTA]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Si la aplicación se bloquea durante una llamada a un archivo DLL del sistema o el código de un tercero, es necesario que encuentre qué archivo DLL estaba activo cuando ocurrió el bloqueo. Si experimenta un bloqueo en un archivo DLL fuera de su propio programa, puede identificar la ubicación mediante el **módulos** ventana.  
  
### <a name="to-find-where-a-crash-occurred-using-the-modules-window"></a>Para averiguar dónde se produjo un bloqueo mediante la ventana Módulos  
  
1.  Anote la dirección donde se produjo el bloqueo.  
  
2.  En el **depurar** menú, elija **Windows**y haga clic en **módulos**.  
  
3.  En el **módulos** ventana, busque la **dirección** columna. Es posible que necesite utilizar la barra de desplazamiento para verla.  
  
4.  Haga clic en el **dirección** situado en la parte superior de la columna para ordenar los archivos DLL por dirección.  
  
5.  Busque en la lista ordenada el archivo DLL cuyo intervalo de direcciones contiene la ubicación del bloqueo.  
  
6.  Examine el **nombre** y **ruta** columnas para ver el nombre del archivo DLL y la ruta de acceso.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: depurar DLL nativas](../debugger/how-to-debug-native-dlls.md)   
 [Cómo: Usar la ventana Módulos](../debugger/how-to-use-the-modules-window.md)





