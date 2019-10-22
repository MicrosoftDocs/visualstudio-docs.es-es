---
title: 'Cómo: crear una aplicación de consola de flujos de trabajo | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: 51a2eea7-921c-49f1-b358-68afc27f1ee9
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1334655f2a8b8587922628664e43784b54ce971
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/19/2019
ms.locfileid: "72604919"
---
# <a name="how-to-create-a-workflow-console-application"></a>Crear una aplicación de consola de flujos de trabajo
[!INCLUDE[wf](../includes/wf-md.md)] le permite crear flujos de trabajo para ejecutar sistemas o procesos humanos. [!INCLUDE[wfd1](../includes/wfd1-md.md)] proporciona la superficie de diseño para la creación de estos flujos de trabajo. El [!INCLUDE[wfd2](../includes/wfd2-md.md)] se puede usar para crear flujos de trabajo desde [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] o se puede integrar en otras aplicaciones que hospedan en otro host el diseñador.

 En este tema se describe cómo usar el [!INCLUDE[wfd2](../includes/wfd2-md.md)] en [!INCLUDE[vs2010](../includes/vs2010-md.md)] para crear un flujo de trabajo en una aplicación de consola.

### <a name="to-create-a-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo

1. Inicie [!INCLUDE[vs2010](../includes/vs2010-md.md)].

2. En el menú **archivo** , seleccione **nuevo**y, a continuación, seleccione **proyecto.** .

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. En el panel **plantillas instaladas** , seleccione **flujo de trabajo** desde las agrupaciones **Visual C#**  o **Visual Basic** , en función del lenguaje de preferencia.

4. En el panel central, seleccione **aplicación de consola de flujos de trabajo**.

5. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

6. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

7. En el cuadro **solución** , escriba el nombre de la nueva solución. Haga clic en **Aceptar** para crear la aplicación.

    > [!NOTE]
    > Si desea agregar una aplicación de consola de flujos de trabajo a una solución existente, ábrala en [!INCLUDE[vs2010](../includes/vs2010-md.md)], haga clic con el botón derecho en la solución en **Explorador de soluciones**y seleccione **Agregar**y luego **nuevo proyecto.** . para abrir el cuadro de diálogo **nuevo proyecto** . Continúe de la forma descrita anteriormente en este procedimiento.

8. La plantilla del proyecto crea una definición de flujo de trabajo en XAML y la definición de la aplicación de consola está en código fuente. El [!INCLUDE[wfd2](../includes/wfd2-md.md)] se abre y muestra el lienzo para el flujo de trabajo que creó.

9. Para crear un flujo de trabajo, arrastre actividades u otros elementos de flujo de trabajo desde el **cuadro de herramientas** a la superficie de diseño del flujo de trabajo.

## <a name="see-also"></a>Vea también
 [Crear un proyecto de flujo de trabajo](../workflow-designer/creating-a-workflow-project.md)