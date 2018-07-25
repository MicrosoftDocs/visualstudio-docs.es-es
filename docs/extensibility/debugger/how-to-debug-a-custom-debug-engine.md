---
title: 'Cómo: Depurar un motor de depuración | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: f15456dddcb18909e514e485e749029c7dac9da9
ms.sourcegitcommit: 25a62c2db771f938e3baa658df8b1ae54a960e4f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2018
ms.locfileid: "39231920"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Cómo: Depurar un motor de depuración personalizado
Un tipo de proyecto inicia el motor de depuración (DE) desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método. Esto significa que se ha iniciado la DE bajo el control de la instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlar el tipo de proyecto. Sin embargo, esa instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no se puede depurar la DE. Las siguientes son los pasos que le permiten depurar su personalizada DE.  
  
> [!NOTE]
>  : En el procedimiento "Depurar un motor de depuración", debe esperar la DE iniciarse antes de que pueden asociarse a ella. Si coloca al principio de la DE que aparece cuando se inicia la DE un cuadro de mensaje, puede adjuntar en ese momento y, a continuación, desactive el cuadro de mensaje para continuar. De este modo, puede detectar todos los eventos DE.  
  
> [!WARNING]
>  Debe tener instalado antes de intentar los siguientes procedimientos de depuración remota. Consulte [depuración remota](../../debugger/remote-debugging.md) para obtener más información.  
  
## <a name="debug-a-custom-debug-engine"></a>Depurar un motor de depuración personalizado  
  
1.  Iniciar *msvsmon.exe*, Monitor de depuración remoto.  
  
2.  Desde el **herramientas** menú *msvsmon.exe*, seleccione **opciones** para abrir el **opciones** cuadro de diálogo.  
  
3.  Seleccione la opción "sin autenticación" y haga clic en **Aceptar**.  
  
4.  Iniciar una instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y abra el proyecto DE personalizado.  
  
5.  Inicie una segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y abra el proyecto personalizado que se inicia la DE (para el desarrollo, esto es generalmente en el subárbol del registro experimental que se haya configurado cuando se instala VSIP).  
  
6.  En esta segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargar un archivo de origen desde el proyecto personalizado e inicie el programa que se desea depurar. Espere unos minutos para permitir que la DE cargar o espere hasta que se alcanza un punto de interrupción.  
  
7.  En la primera instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (con el proyecto DE), seleccione **asociar al proceso** desde el **depurar** menú.  
  
8.  En el **asociar al proceso** cuadro de diálogo, cambie el **transporte** a **remoto (nativo sólo sin autenticación)**.  
  
9. Cambiar el **calificador** al nombre de la máquina (Nota: hay un historial de entradas, por lo que deberá escribir este nombre sólo una vez).  
  
10. En el **procesos disponibles** lista, seleccione la instancia de la DE que se está ejecutando y haga clic en el **adjuntar** botón.  
  
11. Una vez que haya cargado los símbolos en el DE, colocar puntos de interrupción en el código DE.  
  
12. Cada vez que se detenga y reinicie el proceso de depuración, repita los pasos 6 a 10.  
  
## <a name="debug-a-custom-project-type"></a>Depurar un tipo de proyecto personalizado  
  
1.  Iniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el subárbol del registro normal y cargar el proyecto escriba proyecto (Esto es, el origen al tipo de proyecto, no una instancia del tipo de proyecto).  
  
2.  Abra las propiedades del proyecto y vaya a la **depurar** página. Para el **comando**, escriba la ruta de acceso a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (de forma predeterminada, se trata de *[unidad]* \Program Files\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Para el **argumentos de comando**, tipo `/rootsuffix exp` para el subárbol del registro experimental (creado cuando se instaló VSIP).  
  
4.  Haga clic en **Aceptar** para aceptar los cambios.  
  
5.  Inicie el tipo de proyecto presionando **F5**. Esto inicia una segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  En este momento, puede colocar puntos de interrupción en el código de origen del tipo de proyecto.  
  
7.  En la segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargar o crear una nueva instancia del tipo de proyecto. Durante la carga o la creación, se pueden alcanzar los puntos de interrupción.  
  
8.  Depurar el tipo de proyecto.  
  
9. Si elige depurar el proceso de iniciar un DE, puede realizar los pasos del procedimiento "Depurar un motor de depuración" para asociar a la DE una vez que se inicie. Esto le ofrece tres instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ejecutando: uno para el origen del tipo de proyecto, para el tipo de proyecto con instancias y una tercera conectados a la DE segundo.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)