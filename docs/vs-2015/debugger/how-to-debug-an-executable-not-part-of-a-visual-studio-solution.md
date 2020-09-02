---
title: 'Cómo: depurar un archivo ejecutable que no forma parte de una solución de Visual Studio | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: conceptual
dev_langs:
- FSharp
- VB
- CSharp
- C++
- JScript
- VB
- CSharp
- C++
helpviewer_keywords:
- debugging [Visual Studio], executables
- executable files, importing
- executable files, debugging outside of projects
ms.assetid: 3ea176e8-1ce5-42c4-b7a2-abe3a2765033
caps.latest.revision: 26
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: e33233fd313cd6a73013ce55333a860663ddb601
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "65704522"
---
# <a name="how-to-debug-an-executable-not-part-of-a-visual-studio-solution"></a>Cómo: Depurar un archivo ejecutable que no es parte de una solución de Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Es posible que haya ocasiones en las que desee depurar un archivo ejecutable que no forme parte de un proyecto de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Puede tratarse de un archivo ejecutable que se haya creado fuera de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o de un archivo ejecutable que haya recibido de otra persona.  
  
 La solución habitual a este problema consiste en iniciar el archivo ejecutable fuera de Visual Studio y asociarlo mediante el depurador de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Para obtener más información, vea[asociar a procesos en ejecución](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 La asignación a una aplicación requiere algunos pasos que deben realizarse manualmente, por lo que necesitan algunos segundos. Este ligero retraso significa que la asignación no será la solución si se está intentando depurar un problema que se produce durante el inicio. Además, si se depura un programa que no espera que el usuario proporcione datos y finaliza rápidamente, puede que no tenga tiempo de asociar el archivo al programa. En caso de que tenga instalado [!INCLUDE[vcprvc](../includes/vcprvc-md.md)], podrá crear un proyecto EXE para este tipo de programa.  
  
### <a name="to-create-an-exe-project-for-an-existing-executable"></a>Para crear un proyecto .EXE para un archivo ejecutable existente  
  
1. En el menú **archivo** , haga clic en **abrir** y seleccione **proyecto**.  
  
2. En el cuadro de diálogo **Abrir proyecto** , haga clic en la lista desplegable situada junto al cuadro **nombre de archivo** y seleccione **todos los archivos de proyecto**.  
  
3. Busque el archivo ejecutable y haga clic en **Aceptar**.  
  
     De esta manera creará una solución temporal que contiene el archivo ejecutable.  
  
### <a name="to-import-an-executable-into-a-visual-studio-solution"></a>Para importar una archivo ejecutable a una solución de Visual Studio  
  
1. En el menú **archivo** , elija **Agregar proyecto**y, a continuación, haga clic en **proyecto existente**.  
  
2. En el cuadro de diálogo **Agregar proyecto existente** , haga clic en la lista desplegable situada junto al cuadro **nombre de archivo** y seleccione **todos los archivos de proyecto**.  
  
3. Busque y seleccione el archivo ejecutable.  
  
4. Haga clic en **OK**.  
  
5. Inicie el archivo ejecutable mediante la elección de un comando de ejecución, como **iniciar**, en el menú **depurar** .  
  
    > [!NOTE]
    > No todos los lenguajes de programación admiten proyectos EXE. Si necesita utilizar esta característica, instale [!INCLUDE[vcprvc](../includes/vcprvc-md.md)].  
  
     Cuando se depura un archivo ejecutable sin el código fuente, las características de depuración disponibles son limitadas, tanto si se asocia el depurador al archivo en ejecución como si se agrega el archivo ejecutable a una solución de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]. Si el archivo ejecutable se compiló sin información de depuración en un formato compatible, las características disponibles serán aún más limitadas. Si dispone del código fuente, lo más recomendable es que importe dicho código a [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] y que cree una versión de depuración del archivo ejecutable en [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].  
  
## <a name="see-also"></a>Consulte también  
 [Preparación y configuración del depurador](../debugger/debugger-settings-and-preparation.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Archivos DBG](https://msdn.microsoft.com/91e449e9-8b65-4123-960f-2107cd1f1cfd)
