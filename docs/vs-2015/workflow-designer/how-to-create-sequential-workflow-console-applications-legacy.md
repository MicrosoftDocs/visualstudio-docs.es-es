---
title: Procedimiento Crear aplicaciones de consola de flujos de trabajo secuenciales (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, console applications
- sequential workflows, console applications
- console applications, sequential workflow
ms.assetid: 9f7be7fa-551f-42c6-a9bb-f5ae8ab83625
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: f4016597d6c88cfe03ebf823e2fea17730b69562
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60090984"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Procedimiento Crear aplicaciones de consola de flujos de trabajo secuenciales (heredado)
Siga estos pasos para crear un proyecto de aplicación de consola de flujos de trabajo secuenciales mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo secuenciales  
  
1. Inicie Visual Studio.  
  
2. En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3. Seleccione el **.NET Framework 3.0** opción o el **.NET Framework 3.5** opción en la lista desplegable situada en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    >  La opción predeterminada de [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.  
  
4. En el **tipos de proyecto** panel, seleccione proyectos de Visual C# o proyectos de Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.  
  
5. En el **plantillas** panel, seleccione **aplicación de consola de flujo de trabajo secuenciales**.  
  
6. En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7. En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
     Se abrirá el Diseñador de Windows Forms, que mostrará el formulario Form1 del proyecto creado.  
  
8. Haga clic en **Aceptar**.  
  
     Se abre el Diseñador de flujo de trabajo y muestra la superficie de diseño de flujo de trabajo del flujo de trabajo secuencial que ha creado.  
  
9. Arrastre una actividad desde la **cuadro de herramientas** a la superficie de diseño en el **coloque la actividad** área designada.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Desarrollar flujos de trabajo](http://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)