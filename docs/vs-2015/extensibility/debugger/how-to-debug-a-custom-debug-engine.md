---
title: Cómo Depurar un motor de depuración | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7effa937a8faa0a238f8be2505ddf47223010bc1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60039954"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Cómo Depurar un motor de depuración personalizado
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Un tipo de proyecto inicia el motor de depuración (DE) desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método. Esto significa que se ha iniciado la DE bajo el control de la instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] controlar el tipo de proyecto. Sin embargo, esa instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] no se puede depurar la DE. Las siguientes son los pasos para que pueda depurar su personalizada DE.  
  
> [!NOTE]
>  :     En el procedimiento "Depuración de un motor de depuración de personalizado", debe esperar la DE iniciarse antes de que pueden asociarse a ella. Si coloca al principio de la DE que aparece cuando se inicia la DE un cuadro de mensaje, puede adjuntar en ese momento y, a continuación, desactive el cuadro de mensaje para continuar. De este modo, puede detectar todos los eventos DE.  
  
> [!WARNING]
>  Debe tener instalado antes de intentar los siguientes procedimientos de depuración remota. Consulte [depuración remota](../../debugger/remote-debugging.md) para obtener más información.  
  
### <a name="debugging-a-custom-debug-engine"></a>Depuración de un motor de depuración personalizado  
  
1. Iniciar msvsmon.exe, el Monitor de depuración remota.  
  
2. Desde el **herramientas** menú msvsmon.exe, seleccione **opciones** para abrir el **opciones** cuadro de diálogo.  
  
3. Seleccione la opción "sin autenticación" y haga clic en **Aceptar**.  
  
4. Iniciar una instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y abra el proyecto DE personalizado.  
  
5. Inicie una segunda instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] y abra el proyecto personalizado que se inicia la DE (para el desarrollo, esto es generalmente en el subárbol del registro experimental que se haya configurado cuando se instala VSIP).  
  
6. En esta segunda instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], cargar un archivo de origen desde el proyecto personalizado e inicie el programa que se desea depurar. Espere unos minutos para permitir que la DE cargar o espere hasta que se alcanza un punto de interrupción.  
  
7. En la primera instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] (con el proyecto DE), seleccione **asociar al proceso** desde el **depurar** menú.  
  
8. En el **asociar al proceso** cuadro de diálogo, cambie el **transporte** a **remoto (nativo sólo sin autenticación)**.  
  
9. Cambiar el **calificador** al nombre de la máquina (Nota: hay un historial de entradas, por lo que deberá escribir este nombre sólo una vez).  
  
10. En el **procesos disponibles** lista, seleccione la instancia de la DE que se está ejecutando y haga clic en el **adjuntar** botón.  
  
11. Una vez que haya cargado los símbolos en el DE, colocar puntos de interrupción en el código DE.  
  
12. Cada vez que se detenga y reinicie el proceso de depuración, repita los pasos 6 a 10.  
  
### <a name="debugging-a-custom-project-type"></a>Depuración de un tipo de proyecto personalizado  
  
1. Iniciar [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] en el subárbol del registro normal y cargar el proyecto escriba proyecto (Esto es, el origen al tipo de proyecto, no una instancia del tipo de proyecto).  
  
2. Abra las propiedades del proyecto y vaya a la **depurar** página. Para el **comando**, escriba la ruta de acceso a la [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] IDE (de forma predeterminada, se trata de *[unidad]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] 8\Common7\IDE\devenv.exe).  
  
3. Para el **argumentos de comando**, tipo `/rootsuffix exp` para el subárbol del registro experimental (creado cuando se instaló VSIP).  
  
4. Haga clic en **Aceptar** para aceptar los cambios.  
  
5. Inicie el tipo de proyecto presionando F5. Esto iniciará una segunda instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)].  
  
6. En este momento, puede colocar puntos de interrupción en el código de origen del tipo de proyecto.  
  
7. En la segunda instancia de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], cargar o crear una nueva instancia del tipo de proyecto. Durante la carga o la creación, se pueden alcanzar los puntos de interrupción.  
  
8. Depurar el tipo de proyecto.  
  
9. Si elige depurar el proceso de iniciar un DE, puede realizar los pasos del procedimiento de "Depuración de un motor de depuración de personalizado" para asociar a la DE una vez que se inicie. Esto le dará tres instancias de [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] ejecutando: uno para el origen del tipo de proyecto, para el tipo de proyecto con instancias y una tercera conectados a la DE segundo.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
