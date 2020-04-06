---
title: 'Cómo: Depurar un motor de depuración personalizado ? Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, debugging
- debugging [Debugging SDK], custom debug engines
ms.assetid: df27a8d6-3938-45ff-b47f-b684e80b38a0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: c79790bfc9c9cd3767a453258b8c2d340f64d029
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738577"
---
# <a name="how-to-debug-a-custom-debug-engine"></a>Cómo: Depurar un motor de depuración personalizado
Un tipo de proyecto inicia el motor <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg.DebugLaunch%2A> de depuración (DE) desde el método. Esto significa que el DE se lanza bajo [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] el control de la instancia de control del tipo de proyecto. Sin embargo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] esa instancia de no puede depurar el DE. Lo que sigue son los pasos que le permiten depurar su DE personalizado.

> [!NOTE]
> : en el procedimiento "Depurar un motor de depuración personalizado", debe esperar a que se inicie la DE antes de poder adjuntarla. Si coloca un cuadro de mensaje cerca del principio de su DE que aparece cuando se inicia el DE, puede adjuntar en ese punto y, a continuación, desactive el cuadro de mensaje para continuar. De esa manera, puede ver todos los eventos DE.

> [!WARNING]
> Debe tener instalada la depuración remota antes de intentar los siguientes procedimientos. Consulte [Depuración remota](../../debugger/remote-debugging.md) para obtener más información.

## <a name="debug-a-custom-debug-engine"></a>Depurar un motor de depuración personalizado

1. Inicie *msvsmon.exe*, el Monitor de depuración remota.

2. En el menú **Herramientas** de *msvsmon.exe*, seleccione **Opciones** para abrir el cuadro de diálogo **Opciones.**

3. Seleccione la opción "sin autenticación" y haga clic en **Aceptar**.

4. Inicie una [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instancia y abra el proyecto DE personalizado.

5. Inicie una segunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instancia del proyecto personalizado que inicia el DE (para el desarrollo, esto suele estar en el subárbol del registro experimental que se configura cuando se instala VSIP).

6. En esta segunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instancia de , cargue un archivo de origen desde el proyecto personalizado e inicie el programa que se va a depurar. Espere unos momentos para permitir que el DE se cargue o espere hasta que se golpee un punto de interrupción.

7. En la primera [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] instancia de (con el proyecto DE), seleccione **Adjuntar al proceso** en el menú **Depurar.**

8. En el cuadro de diálogo **Asociar al proceso,** cambie **Transporte** a **remoto (nativo solo sin autenticación).**

9. Cambie el **Calificador** por el nombre de su máquina (tenga en cuenta que hay un historial de entradas, por lo que debe escribir este nombre solo una vez).

10. En la lista **Procesos disponibles,** seleccione la instancia de su DE que se está ejecutando y haga clic en el botón **Adjuntar.**

11. Después de que los símbolos se hayan cargado en su DE, coloque puntos de interrupción en el código DE.

12. Cada vez que detenga y reinicie el proceso de depuración, repita los pasos del 6 al 10.

## <a name="debug-a-custom-project-type"></a>Depurar un tipo de proyecto personalizado

1. Comience [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] en el subárbol del Registro normal y cargue el proyecto de tipo de proyecto (esto es el origen del tipo de proyecto, no una creación de instancias del tipo de proyecto).

2. Abra las propiedades del proyecto y vaya a la página **Depurar.** Para el **comando**, escriba [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] la ruta de acceso al IDE (de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] forma predeterminada, se trata de *[unidad]*.

3. En **Command Arguments** `/rootsuffix exp` , escriba para el subárbol del Registro experimental (creado cuando se instaló VSIP).

4. Haga clic en **Aceptar** para aceptar los cambios.

5. Inicie el tipo de proyecto presionando **F5**. Esto lanza una segunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instancia de .

6. En este punto, puede colocar puntos de interrupción en el código fuente del tipo de proyecto.

7. En la segunda [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]instancia de , cargue o cree una nueva instancia del tipo de proyecto. Durante la carga o la creación, los puntos de interrupción pueden ser alcanzados.

8. Depurar el tipo de proyecto.

9. Si decide depurar el proceso de iniciar un DE, puede realizar los pasos del procedimiento "Depurar un motor de depuración personalizado" para adjuntar lo desenmarcha después de iniciarlo. Esto proporciona tres instancias de [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ejecución: una para el origen de tipo de proyecto, una segunda para el tipo de proyecto con instancias y una tercera asociada a la DE.

## <a name="see-also"></a>Vea también
- [Creación de un motor de depuración personalizado](../../extensibility/debugger/creating-a-custom-debug-engine.md)
