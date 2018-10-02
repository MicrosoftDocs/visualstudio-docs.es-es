---
title: 'Cómo: depurar en modo mixto | Microsoft Docs'
ms.custom: ''
ms.date: 2018-06-30
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
- C++
helpviewer_keywords:
- debugging DLLs
- debugging [Visual Studio], mixed-mode
- mixed-mode debugging
ms.assetid: 2859067d-7fcc-46b0-a4df-8c2101500977
caps.latest.revision: 32
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 1ce056b60a3e080490a2ad60f4aee5a7b5c8dd63
ms.sourcegitcommit: 55f7ce2d5d2e458e35c45787f1935b237ee5c9f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "47566782"
---
# <a name="how-to-debug-in-mixed-mode"></a>Cómo: Depurar en modo mixto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

La versión más reciente de este tema puede encontrarse en [Cómo: depurar en modo mixto](https://docs.microsoft.com/visualstudio/debugger/how-to-debug-in-mixed-mode).  
  
Los procedimientos siguientes describen cómo depurar código administrado y nativo, también conocido como depuración en modo mixto. Existen dos escenarios para hacerlo, en función de que el archivo DLL o la aplicación se hayan escrito en código nativo:  
  
-   La aplicación que realiza la llamada al archivo DLL está escrita en código nativo. En este caso, el código del archivo DLL será administrado y deberán habilitarse tanto los depuradores administrados como los nativos para depurar ambos tipos de código. Puede comprobarlo en el  **\<proyecto > páginas de propiedades** cuadro de diálogo. La forma de hacerlo depende de si inicia la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada.  
  
-   La aplicación que realiza la llamada al archivo DLL está escrita en código administrado y el archivo DLL está escrito en código nativo.  
  
> [!NOTE]
>  Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo en Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Para habilitar la depuración en modo mixto  
  
1.  En **el Explorador de soluciones**, seleccione el proyecto.  
  
2.  En el **vista** menú, haga clic en **páginas de propiedades**.  
  
3.  En el  **\<proyecto > páginas de propiedades** cuadro de diálogo, expanda el **propiedades de configuración** nodo y, a continuación, seleccione **depuración**.  
  
4.  Establecer **el tipo de depurador** a **mixto** o **automática**.  
  
## <a name="see-also"></a>Vea también  
 [Cómo: Depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)



