---
title: "Cómo: depurar en modo mixto | Documentos de Microsoft"
ms.custom: 
ms.date: 06/19/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "29"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e319f0e6c9ca6197930858407a2177e9fe246907
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-debug-in-mixed-mode"></a>Cómo: Depurar en modo mixto
Los procedimientos siguientes describen cómo depurar código administrado y nativo, también conocido como depuración en modo mixto. Existen dos escenarios para hacerlo, en función de que el archivo DLL o la aplicación se hayan escrito en código nativo:  
  
-   La aplicación que realiza la llamada al archivo DLL está escrita en código nativo. En este caso, el código del archivo DLL será administrado y deberán habilitarse tanto los depuradores administrados como los nativos para depurar ambos tipos de código. Puede comprobarlo el  **\<proyecto > páginas de propiedades** cuadro de diálogo. La forma de hacerlo depende de si inicia la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada.  
  
-   La aplicación que realiza la llamada al archivo DLL está escrita en código administrado y el archivo DLL está escrito en código nativo.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para más información, vea [Personalizar el IDE de Visual Studio](../ide/personalizing-the-visual-studio-ide.md).

Si no tiene acceso al proyecto de la aplicación que realiza la llamada, puede depurar un archivo DLL desde el proyecto DLL. Para obtener más información, consulta [How to: Debug from a DLL Project](../debugger/how-to-debug-from-a-dll-project.md). No es necesario usar mixto para depurar el proyecto de DLL.
  
### <a name="to-enable-mixed-mode-debugging-c-calling-app"></a>Para habilitar la depuración en modo mixto (aplicación de llamada de C++)  
  
1.  En **el Explorador de soluciones**, seleccione el proyecto nativo.
  
2.  En el **vista** menú, haga clic en **páginas de propiedades**.
  
3.  En el  **\<proyecto > páginas de propiedades** cuadro de diálogo, expanda el **propiedades de configuración** nodo y, a continuación, seleccione **depuración**.  
  
4.  Establecer **el tipo de depurador** a **mixto** o **automática**.

    ![Habilitar la depuración en modo mixto](../debugger/media/dbg-mixed-mode-from-native.png "habilitar la depuración en modo mixto")

### <a name="to-enable-mixed-mode-debugging-c-or-vb-calling-app"></a>Para habilitar la depuración en modo mixto (C# o VB aplicación que realiza la llamada)  
  
1.  En **el Explorador de soluciones**, seleccione el proyecto administrado.  
  
2.  En el **vista** menú, haga clic en **páginas de propiedades**.  
  
3.  En el  **\<proyecto > páginas de propiedades** cuadro de diálogo, seleccione la **depurar** pestaña y, a continuación, seleccione **habilitar la depuración de código nativo**

    ![Habilitar la depuración de código nativo](../debugger/media/dbg-mixed-mode-from-csharp.png "habilitar la depuración de código nativo")
  
## <a name="see-also"></a>Vea también  
 [Cómo: Depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)