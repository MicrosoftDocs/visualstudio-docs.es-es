---
title: 'Cómo: depurar archivos DLL nativos | Microsoft Docs'
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
ms.openlocfilehash: 16a533b27e619526edab71374d922e68baf0a4b0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65702678"
---
# <a name="how-to-debug-native-dlls"></a>Cómo: Depurar DLL nativas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija Importar y exportar configuraciones en el menú Herramientas. Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Cuando se depura un archivo DLL, se puede iniciar la depuración desde:  
  
- El proyecto utilizado para crear el archivo ejecutable que llama al archivo DLL.  
  
  \- o -  
  
- El proyecto utilizado para crear el propio archivo DLL.  
  
  Si tiene el proyecto utilizado para crear el archivo ejecutable, inicie la depuración desde ese proyecto. Puede abrir entonces un archivo de código fuente para el archivo DLL y establecer puntos de interrupción en ese archivo, aunque no forme parte del proyecto utilizado para crear el archivo ejecutable. Para obtener más información, vea [Puntos de interrupción](https://msdn.microsoft.com/fe4eedc1-71aa-4928-962f-0912c334d583).  
  
  Si está depurando desde el proyecto que crea el archivo DLL, debe especificar el archivo ejecutable que desea utilizar en la depuración del archivo DLL.  
  
### <a name="to-specify-an-executable-for-the-debug-session"></a>Para especificar un archivo ejecutable para la sesión de depuración  
  
1. En **Explorador de soluciones**, seleccione el proyecto que crea el archivo dll.  
  
2. En el menú **Ver** , elija**páginas de propiedades**.  
  
3. En el cuadro de diálogo **páginas de propiedades** , abra la carpeta **propiedades de configuración** y seleccione la categoría **depuración** .  
  
4. En el cuadro **comando** , especifique el nombre de la ruta de acceso del contenedor. Por ejemplo, C:\Archivos de programa\MiAplicación\MIAPLIC.EXE.  
  
5. En el cuadro **argumentos del comando** , especifique los argumentos necesarios para el ejecutable.  
  
   Si no especifica el archivo ejecutable en el cuadro de diálogo**páginas de propiedades** del _proyecto_, el [cuadro de diálogo ejecutable para la sesión de depuración](../debugger/executable-for-debugging-session-dialog-box.md) aparece cuando se inicia la depuración.  
  
## <a name="see-also"></a>Consulte también  
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Depurar en Visual Studio](../debugger/debugging-in-visual-studio.md)
