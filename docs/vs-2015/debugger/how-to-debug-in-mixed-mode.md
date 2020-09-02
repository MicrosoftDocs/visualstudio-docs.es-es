---
title: Procedimiento Depuración en modo mixto | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
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
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: c5e2dd4ea0000eefdbd9f74c8fa97c4c63e06fab
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65681144"
---
# <a name="how-to-debug-in-mixed-mode"></a>Cómo: Depurar en modo mixto
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Los procedimientos siguientes describen cómo depurar código administrado y nativo, también conocido como depuración en modo mixto. Existen dos escenarios para hacerlo, en función de que el archivo DLL o la aplicación se hayan escrito en código nativo:  
  
- La aplicación que realiza la llamada al archivo DLL está escrita en código nativo. En este caso, el código del archivo DLL será administrado y deberán habilitarse tanto los depuradores administrados como los nativos para depurar ambos tipos de código. Puede comprobarlo en el cuadro de diálogo ** \<Project> páginas de propiedades** . La forma de hacerlo depende de si inicia la depuración desde el proyecto DLL o desde el proyecto de la aplicación que hace la llamada.  
  
- La aplicación que realiza la llamada al archivo DLL está escrita en código administrado y el archivo DLL está escrito en código nativo.  
  
> [!NOTE]
> Los cuadros de diálogo y comandos de menú que se ven pueden diferir de los descritos en la Ayuda, en función de los valores de configuración o de edición activos. Para cambiar la configuración, elija la opción **Importar y exportar configuraciones** del menú **Herramientas** . Para obtener más información, consulte [Personalizar la configuración de desarrollo de Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-enable-mixed-mode-debugging"></a>Para habilitar la depuración en modo mixto  
  
1. En **Explorador de soluciones**, seleccione el proyecto.  
  
2. En el menú **Ver**, haga clic en **Páginas de propiedades**.  
  
3. En el cuadro de diálogo ** \<Project> páginas de propiedades** , expanda el nodo **propiedades de configuración** y, a continuación, seleccione **depuración**.  
  
4. Establezca el **Tipo de depurador** en **Mixto** o **Automático**.  
  
## <a name="see-also"></a>Consulte también  
 [Cómo: depurar desde un proyecto DLL](../debugger/how-to-debug-from-a-dll-project.md)
