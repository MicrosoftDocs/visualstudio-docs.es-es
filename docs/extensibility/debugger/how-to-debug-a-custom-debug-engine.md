---
title: "C&#243;mo: Depurar un motor de depuraci&#243;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motores de depuración, depuración"
  - "depurar [SDK de depuración], motores de depuración personalizados"
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# C&#243;mo: Depurar un motor de depuraci&#243;n
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un tipo de proyecto inicia el motor de depuración \(DE\) del método de <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> .  Esto significa que el OF se inicia bajo el control de la instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] que controla el tipo de proyecto.  Sin embargo, esa instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] no puede depurar el OF.  Los siguientes son los pasos que permiten depurar custom OF.  
  
> [!NOTE]
>  :     En el procedimiento “debug del motor de depuración”, debe esperar el OF para iniciar antes de poder asociar el.  Si coloca un cuadro de mensaje cerca del principio de que se produce cuando el OF inicia, puede adjuntar en ese punto y luego borre el cuadro de mensaje continuar.  De ese modo, puede detectar a todo el OF events.  
  
> [!WARNING]
>  Debe realizar la depuración remota instalar antes de intentar los procedimientos siguientes.  Para obtener información más detallada, vea [Depuración remota](../../debugger/remote-debugging.md).  
  
### Depurar un motor de depuración  
  
1.  Inicio msvsmon.exe, el Monitor de depuración remota.  
  
2.  En el menú de **Herramientas** en msvsmon.exe, **Opciones** seleccione para abrir el cuadro de diálogo de **Opciones** .  
  
3.  Seleccione la opción y haga clic en **Aceptar**de “ninguna autenticación”.  
  
4.  Iniciar una instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y abra el OF personalizado project.  
  
5.  Inicie una segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] y abra el proyecto personalizado que inicia el OF \(para desarrollo, éste es normalmente en el subárbol experimental del registro que está configurado cuando VSIP está instalado\).  
  
6.  En esta segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue un archivo de código fuente del proyecto personalizado y inicie el programa que se va a depurar.  Espere unos momentos para permitir que el OF cargue, o espere hasta un punto de interrupción se alcanza.  
  
7.  En primer lugar de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] \(con el OF project\), seleccione **Adjuntar a procesar** de menú de **Depurar** .  
  
8.  en el cuadro de diálogo de **Adjuntar a procesar** , cambie **transporte** a **Remoto \(sólo para código nativo sin autenticación\)**.  
  
9. Cambie **calificador** al nombre del equipo \(nota: hay un historial de entradas, por lo que debe escribir en este nombre sólo una vez\).  
  
10. En la lista de **Procesos disponibles** , seleccione la instancia de que está ejecutando y haga clic en el botón de **Asociar** .  
  
11. Después de que los símbolos han cargado en el OF, los puntos de interrupción del lugar en el OF code.  
  
12. Cada vez que se detiene y reiniciar el proceso de depuración, repita los pasos 6 a 10.  
  
### depurar un tipo de proyecto personalizado  
  
1.  Inicie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el subárbol normal del registro y cargue el proyecto del tipo de proyecto \(esto es, el origen al tipo de proyecto, no una instancia del tipo de proyecto\).  
  
2.  Abra las propiedades del proyecto y vaya a la página de **Depurar** .  Para el comando, escriba la ruta de acceso a [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE \(de forma predeterminada, éste es *\[\] unidad*\\Program Files\\Microsoft [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] 8 \\Common7\\IDE \\ devenv.exe\).  
  
3.  Para **Argumentos del comando**, `/rootsuffix exp` escrito para el subárbol experimental de registro \(creada cuando VSIP se instaló\).  
  
4.  Haga clic en **Aceptar** para aceptar los cambios.  
  
5.  Inicie el tipo de proyecto presionando F5.  Esto iniciará una segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
6.  En este punto, puede colocar puntos de interrupción en el código fuente del tipo de proyecto.  
  
7.  En la segunda instancia de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], cargue o cree una nueva instancia del tipo de proyecto.  Durante la carga o creación, los puntos de interrupción pueden ser alcanzan.  
  
8.  Depurar el tipo de proyecto.  
  
9. Si elige para depurar el proceso de iniciar un OF, puede realizar los pasos de procedimiento “debug del motor de depuración” para asociar el OF después de que se inicie.  esto le dará tres instancias de ejecutarse de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] : uno para el origen del tipo de proyecto, un segundo para el tipo de proyecto creado instancias, y una tercera adjuntado a OF.  
  
## Vea también  
 [Creación de un motor de depuración](../../extensibility/debugger/creating-a-custom-debug-engine.md)