---
title: 'Cómo: Depurar un motor de depuración personalizado | Documentos de Microsoft'
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
ms.openlocfilehash: 95a2db2bc5e8990f536abc851941c337a1dee277
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Cómo: Depurar un motor de depuración personalizadas
Un tipo de proyecto inicia el motor de depuración (Alemania) desde el <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> método. Esto significa que se ha iniciado el Alemania bajo el control de la instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] controlar el tipo de proyecto. Sin embargo, esa instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no puede depurar el Alemania. A continuación es los pasos para que pueda depurar su Alemania personalizado.  
  
> [!NOTE]
>  : En el procedimiento "Depuración de un motor de depuración de personalizado", debe esperar a que la DE iniciarse antes de que pueden asociarse a ella. Si coloca un cuadro de mensaje al principio de su Alemania que aparece cuando se inicia el Alemania, puede adjuntar en ese momento y, a continuación, desactive el cuadro de mensaje para continuar. De este modo, puede detectar todos los eventos de Alemania.  
  
> [!WARNING]
>  Debe tener instalado antes de intentar los siguientes procedimientos de depuración remota. Vea [depuración remota](../../debugger/remote-debugging.md) para obtener más información.  
  
### <a name="debugging-a-custom-debug-engine"></a>Depuración de un motor de depuración personalizadas  
  
1.  Iniciar msvsmon.exe, el Monitor de depuración remota.  
  
2.  Desde el **herramientas** menú msvsmon.exe, seleccione **opciones** para abrir el **opciones** cuadro de diálogo.  
  
3.  Seleccione la opción "sin autenticación" y haga clic en **Aceptar**.  
  
4.  Iniciar una instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y abra el proyecto DE personalizado.  
  
5.  Inicie una segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y abra el proyecto personalizado que se inicia el Alemania (para el desarrollo, esto es generalmente en el subárbol del registro experimental que se configura cuando se instala VSIP).  
  
6.  En esta segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargar un archivo de origen desde el proyecto personalizado e inicie el programa que desea depurar. Espere unos minutos para permitir que la DE cargar o espere hasta que se alcanza un punto de interrupción.  
  
7.  En la primera instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (con el proyecto DE), seleccione **adjuntar al proceso** desde el **depurar** menú.  
  
8.  En el **adjuntar al proceso** cuadro de diálogo, cambie el **transporte** a **remoto (nativo sólo sin autenticación)**.  
  
9. Cambiar el **calificador** al nombre de la máquina (Nota: hay un historial de entradas, por lo que debe escribir en este nombre de una sola vez).  
  
10. En el **procesos disponibles** , seleccione la instancia de la DE que se está ejecutando y haga clic en el **adjuntar** botón.  
  
11. Una vez que haya cargado los símbolos en su Alemania, colocar puntos de interrupción en el código DE.  
  
12. Cada vez que detenga y reinicie el proceso de depuración, repita los pasos del 6 al 10.  
  
### <a name="debugging-a-custom-project-type"></a>Depuración de un tipo de proyecto personalizadas  
  
1.  Iniciar [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el subárbol del registro normal y la carga el proyecto de tipo de proyecto (Esto es, el origen para el tipo de proyecto, no una instancia de su tipo de proyecto).  
  
2.  Abra las propiedades del proyecto y vaya a la **depurar** página. Para el **comando**, escriba la ruta de acceso a la [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE (de forma predeterminada, es *[unidad]*\Program [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8\Common7\IDE\devenv.exe).  
  
3.  Para el **argumentos del comando**, tipo `/rootsuffix exp` para el subárbol del registro experimental (creado cuando se instaló VSIP).  
  
4.  Haga clic en **Aceptar** para aceptar los cambios.  
  
5.  Inicie el tipo de proyecto al presionar F5. Se iniciará una segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  En este momento, puede colocar puntos de interrupción en el código de origen del tipo de proyecto.  
  
7.  En la segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargar o crear una nueva instancia de su tipo de proyecto. Durante la creación o carga, se pueden alcanzar los puntos de interrupción.  
  
8.  Depurar el tipo de proyecto.  
  
9. Si elige depurar el proceso de iniciar un Alemania, puede realizar los pasos del procedimiento "Depuración de un motor de depuración de personalizado" para adjuntar a la DE una vez que se inicia. Esto le proporcionará tres instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ejecutando: uno para el origen de tipo de proyecto, otro para el tipo de proyecto crea una instancia y un tercero que se adjunta a la DE.  
  
## <a name="see-also"></a>Vea también  
 [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)