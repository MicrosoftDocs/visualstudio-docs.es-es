---
title: 'Cómo: depurar un ejecutable que no forma parte de una solución de Visual Studio | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- CSharp
- VB
- FSharp
- C++
- JScript
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- multiple
ms.openlocfilehash: ce84c4acdc2cf4324c76dbbf7fe0b39ca9715b3c
ms.sourcegitcommit: 1ab675a872848c81a44d6b4bd3a49958fe673c56
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44279107"
---
# <a name="how-to-debug-an-executable-that-is-not-part-of-a-visual-studio-solution"></a>Cómo: depurar un ejecutable que no forma parte de una solución de Visual Studio
En ocasiones, es posible que desea depurar un archivo ejecutable (archivo .exe) que no es parte de un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] proyecto. Puede tratarse de un archivo ejecutable que se haya creado fuera de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] o de un archivo ejecutable que haya recibido de otra persona.  
  
La solución habitual a este problema consiste en iniciar el archivo ejecutable fuera de Visual Studio y asociarlo mediante el depurador de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Para obtener más información, consulte [adjuntar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
La asignación a una aplicación requiere algunos pasos que deben realizarse manualmente, por lo que necesitan algunos segundos. Este ligero retraso significa que la asignación no será la solución si se está intentando depurar un problema que se produce durante el inicio. Además, si se depura un programa que no espera que el usuario proporcione datos y finaliza rápidamente, puede que no tenga tiempo de asociar el archivo al programa. Si tiene [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] y [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)] instalado, puede crear un proyecto EXE para este tipo de programa.

> [!NOTE]
>  No todos los lenguajes de programación admiten proyectos EXE.

Cuando se depura un archivo ejecutable que no forma parte de la solución de Visual Studio, las características de depuración disponibles pueden ser limitadas, ya que adjuntar a un archivo ejecutable que se ejecuta o para agrega el archivo ejecutable para un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] solución.

- Si dispone del código fuente, lo más recomendable es que importe dicho código a [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] y que cree una versión de depuración del archivo ejecutable en [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].
- Si no tiene el código fuente, y si el archivo ejecutable se compiló sin [información de depuración](../debugger/how-to-set-debug-and-release-configurations.md) en un formato compatible, las características de depuración disponibles son muy limitadas. 
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Para crear un proyecto .EXE para un archivo ejecutable existente  
  
1.  En el **archivo** menú, haga clic en **abierto** y seleccione **proyecto**.  
  
2.  En el **Abrir proyecto** cuadro de diálogo, haga clic en la lista desplegable lista situada junto a la **nombre de archivo** cuadro y seleccione **todos los archivos de proyecto**.  
  
3.  Busque el archivo ejecutable y haga clic en **Aceptar**.  

    De esta manera creará una solución temporal que contiene el archivo ejecutable.

5.  Inicie el archivo ejecutable eligiendo un comando de ejecución, como **iniciar**, desde el **depurar** menú.    
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Para importar una archivo ejecutable a una solución de Visual Studio  
  
1.  En el **archivo** menú, elija **Agregar proyecto**y, a continuación, haga clic en **proyecto existente**.  
  
2.  En el **Agregar proyecto existente** cuadro de diálogo, haga clic en la lista desplegable lista situada junto a la **nombre de archivo** cuadro y seleccione **todos los archivos de proyecto**.  
  
3.  Busque y seleccione el archivo ejecutable.  
  
4.  Haga clic en **Aceptar**.  
  
5.  Inicie el archivo ejecutable eligiendo un comando de ejecución, como **iniciar**, desde el **depurar** menú.    
  
## <a name="see-also"></a>Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [DBG (archivos)](/previous-versions/visualstudio/visual-studio-2010/da528y14(v=vs.100))