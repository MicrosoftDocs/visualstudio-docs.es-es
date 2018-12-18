---
title: 'Cómo: crear una aplicación de consola de flujo de trabajo | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: .net-framework-4.6
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: erikre
ms.openlocfilehash: ad509e0e57f2c8996c13ffbe1d8f8890d2954dec
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49251672"
---
# <a name="how-to-create-a-workflow-console-application"></a>Crear una aplicación de consola de flujos de trabajo
[!INCLUDE[wf](../includes/wf-md.md)] le permite crear flujos de trabajo para ejecutar sistemas o procesos humanos. [!INCLUDE[wfd1](../includes/wfd1-md.md)] proporciona la superficie de diseño para la creación de estos flujos de trabajo. El [!INCLUDE[wfd2](../includes/wfd2-md.md)] se puede usar para crear flujos de trabajo desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o se puede integrar en otras aplicaciones que hospedan en otro host el diseñador.  
  
 En este tema se describe cómo usar el [!INCLUDE[wfd2](../includes/wfd2-md.md)] en [!INCLUDE[vs2010](../includes/vs2010-md.md)] para crear un flujo de trabajo en una aplicación de consola.  
  
### <a name="to-create-a-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo  
  
1.  Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].  
  
2.  En el **archivo** menú, elija **New**y, a continuación, seleccione **proyecto...** .  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3.  En el **plantillas instaladas** panel, seleccione **flujo de trabajo** desde el **Visual C#** o **Visual Basic** agrupaciones, dependiendo de su idioma de preferencia.  
  
4.  En el panel central, seleccione **aplicación de consola de flujos de trabajo**.  
  
5.  En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
6.  En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
7.  En el **solución** cuadro, escriba el nombre para la nueva solución. Haga clic en **Aceptar** para crear la aplicación.  
  
    > [!NOTE]
    >  Si desea agregar una aplicación de consola de flujo de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)], haga clic en la solución de **el Explorador de soluciones**y seleccione **agregar**, a continuación,  **Nuevo proyecto...** Para abrir el **nuevo proyecto** cuadro de diálogo. Continúe de la forma descrita anteriormente en este procedimiento.  
  
8.  La plantilla del proyecto crea una definición de flujo de trabajo en XAML y la definición de la aplicación de consola está en código fuente. El [!INCLUDE[wfd2](../includes/wfd2-md.md)] se abre y muestra el lienzo para el flujo de trabajo que creó.  
  
9. Para crear un flujo de trabajo, arrastre actividades u otros elementos de flujo de trabajo desde el **cuadro de herramientas** a la superficie de diseño del flujo de trabajo.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)