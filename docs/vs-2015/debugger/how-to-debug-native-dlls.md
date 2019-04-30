---
title: Procedimiento Depurar archivos DLL nativos | Documentos de Microsoft
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
- debugging DLLs
- DLLs, debugging
- executable files, specifying for debug sessions
ms.assetid: 76b34d15-a66d-4963-842e-c8b955c81696
caps.latest.revision: 20
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: ea2f40119425cc558b5486a9085b92b05ba81c97
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63426521"
---
# <a name="how-to-debug-native-dlls"></a>Procedimiento Depurar archivos DLL nativos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Cuando se depura un archivo DLL, se puede iniciar la depuración desde:  
  
- El proyecto utilizado para crear el archivo ejecutable que llama al archivo DLL.  
  
  \- o -  
  
- El proyecto utilizado para crear el propio archivo DLL.  
  
  Si tiene el proyecto utilizado para crear el archivo ejecutable, inicie la depuración desde ese proyecto. Puede abrir entonces un archivo de código fuente para el archivo DLL y establecer puntos de interrupción en ese archivo, aunque no forme parte del proyecto utilizado para crear el archivo ejecutable. Para obtener más información, vea [Puntos de interrupción](http://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Si está depurando desde el proyecto que crea el archivo DLL, debe especificar el archivo ejecutable que desea utilizar en la depuración del archivo DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Para especificar un archivo ejecutable para la sesión de depuración  
  
1. En **el Explorador de soluciones**, seleccione el proyecto que crea el archivo DLL.  
  
2. Desde el **vista** menú, elija**páginas de propiedades**.  
  
3. En el **páginas de propiedades** cuadro de diálogo, abra el **propiedades de configuración** carpeta y seleccione el **depuración** categoría.  
  
4. En el **comando** cuadro, especifique el nombre de ruta de acceso para el contenedor. Por ejemplo, C:\Archivos de programa\MiAplicación\MIAPLIC.EXE.  
  
5. En el **argumentos de comando** , especifique los argumentos necesarios para el archivo ejecutable.  
  
   Si no especifica el archivo ejecutable en el _proyecto_**páginas de propiedades** cuadro de diálogo, el [ejecutable para el cuadro de diálogo de sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md) aparece al iniciar la depuración.  
  
## <a name="see-also"></a>Vea también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
