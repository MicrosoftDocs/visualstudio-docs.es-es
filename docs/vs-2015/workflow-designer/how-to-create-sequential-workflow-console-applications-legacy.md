---
title: 'Cómo: crear aplicaciones de consola de flujos de trabajo secuenciales (heredado) | Microsoft Docs'
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c9e3f97021e742db7b22a400dee0682669b07e4c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662728"
---
# <a name="how-to-create-sequential-workflow-console-applications-legacy"></a>Cómo: Crear aplicaciones de consola de flujos de trabajo secuenciales (Heredado)
Siga estos pasos para crear un proyecto de aplicación de consola de flujos de trabajo secuenciales mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].

### <a name="to-create-a-sequential-workflow-console-application"></a>Para crear una aplicación de consola de flujos de trabajo secuenciales

1. Inicie Visual Studio.

2. En el menú **Archivo** , seleccione **Nuevo**y haga clic en **Proyecto**.

     Aparece el cuadro de diálogo **Nuevo proyecto** .

3. Seleccione la opción **.NET Framework 3,0** o la opción **.NET Framework 3,5** en la lista desplegable de la parte superior de la ventana **nuevo proyecto** para obtener acceso al diseñador heredado.

    > [!NOTE]
    > La opción predeterminada en [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.

4. En el panel **tipos de proyecto** , seleccione proyectos de Visual C# o proyectos de Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.

5. En el panel **plantillas** , seleccione **aplicación de consola de flujos de trabajo secuenciales**.

6. En el cuadro **nombre** , escriba un nombre descriptivo para el proyecto con el fin de facilitar su identificación.

7. En el cuadro **Ubicación** , escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.

     Se abrirá el Diseñador de Windows Forms, que mostrará el formulario Form1 del proyecto creado.

8. Haga clic en **Aceptar**.

     Se abre el Diseñador de flujo de trabajo y muestra la superficie de diseño de flujo de trabajo del flujo de trabajo secuencial que ha creado.

9. Arrastre una actividad del **cuadro de herramientas** a la superficie de diseño del área de colocación de la **actividad** designada.

## <a name="see-also"></a>Consulte también
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md) [desarrollar flujos de trabajo](https://msdn.microsoft.com/557bcb1f-a7ab-49f6-8df7-2706b7001301)