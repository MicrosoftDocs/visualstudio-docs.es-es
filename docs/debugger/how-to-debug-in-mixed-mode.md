---
title: 'Cómo: depurar en modo mixto | Microsoft Docs'
ms.custom: ''
ms.date: 06/19/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: 8a08cf3cf95073d06c1dfa350f2de86bf72837c5
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49182681"
---
# <a name="how-to-debug-in-mixed-mode"></a>Cómo: depurar en modo mixto
Los procedimientos siguientes describen cómo habilitar la depuración para depurar código administrado y nativo, así como también se denomina mixto. Hay dos escenarios de depuración en modo mixto:  
  
- La aplicación que llama a un archivo DLL está escrita en código nativo y el archivo DLL administrado. 
  
- La aplicación que llama a un archivo DLL está escrita en código administrado y el archivo DLL está en código nativo. Para ver un tutorial que le guiará a través de este escenario con más detalle, consulte [depurar código administrado y nativo](../debugger/how-to-debug-managed-and-native-code.md).
   
Puede habilitar los depuradores administrados y nativos en el proyecto de aplicación que realiza la llamada **propiedad** páginas. Los valores difieren entre las aplicaciones nativas y administradas. 

Si no tiene acceso al proyecto de una aplicación que realiza la llamada, se puede depurar la DLL desde el proyecto DLL. No es necesario un modo mixto para depurar solo el proyecto DLL. Para obtener más información, consulte [Cómo: depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md). 

> [!NOTE]
> Los cuadros de diálogo y comandos que se ven pueden diferir de los incluidos en este artículo, dependiendo de la edición o configuración de Visual Studio. Para cambiar la configuración, elija **herramientas** > **importar y exportar configuraciones**. Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

## <a name="enable-mixed-mode-debugging-for-a-native-calling-app"></a>Habilitar la depuración en modo mixto para una aplicación nativa que realiza la llamada  
  
1. Seleccione el proyecto de C++ en **el Explorador de soluciones** y haga clic en el **propiedades** icono, presione **Alt**+**ENTRAR**, o Haga clic en y elija **propiedades**.
   
1. En el  **\<proyecto > páginas de propiedades** cuadro de diálogo, expanda **propiedades de configuración**y, a continuación, seleccione **depuración**.  
   
1. Establecer **el tipo de depurador** a **mixto** o **automática**.
   
1. Seleccione **Aceptar**.
   
   ![Habilitar la depuración en modo mixto](../debugger/media/dbg-mixed-mode-from-native.png "habilitar la depuración en modo mixto")

## <a name="enable-mixed-mode-debugging-for-a-managed-calling-app"></a>Habilitar la depuración en modo mixto para una aplicación que realiza la llamada administrada  
  
1. Seleccione el proyecto de C# o Visual Basic en **el Explorador de soluciones** y seleccione el **propiedades** icono, presione **Alt**+**ENTRAR**, o bien haga clic en y elija **propiedades**.
   
1. Seleccione el **depurar** pestaña y, a continuación, seleccione **Habilitar depuración de código nativo**.
   
1. Use **archivo** > **guardar los elementos seleccionados** o **CTRL+s** para guardar los cambios.

   ![Habilitar depuración de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "Habilitar depuración de código nativo")
  
## <a name="see-also"></a>Vea también  
 [Depuración desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)