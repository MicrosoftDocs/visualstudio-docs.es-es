---
title: Procedimiento Crear una biblioteca de flujos de trabajo secuenciales (heredado) | Documentos de Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- sequential workflows, creating library
- workflows, sequential workflow library
- projects, sequential workflow library
- sequential workflow libraries
ms.assetid: 9433ccf3-1eab-4d53-90ff-2e7b2341676c
caps.latest.revision: 5
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 6563c209dfd86a74c2d51fc9179948c63e7cf4b2
ms.sourcegitcommit: 08fc78516f1107b83f46e2401888df4868bb1e40
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65686690"
---
# <a name="how-to-create-a-sequential-workflow-library-legacy"></a>Procedimiento Crear una biblioteca de flujos de trabajo secuenciales (heredado)
Siga estos pasos para crear un proyecto de biblioteca de flujos de trabajo secuenciales mediante el uso de [!INCLUDE[wfd1](../includes/wfd1-md.md)] heredado proporcionado por [!INCLUDE[vs2010](../includes/vs2010-md.md)]. Use el [!INCLUDE[wfd2](../includes/wfd2-md.md)] heredado cuando deba tener como destino [!INCLUDE[netfx35_long](../includes/netfx35-long-md.md)] o [!INCLUDE[vstecwinfx](../includes/vstecwinfx-md.md)].  
  
### <a name="to-create-a-sequential-workflow-library-project"></a>Para crear un proyecto de biblioteca de flujos de trabajo secuenciales  
  
1. Inicie Visual Studio.  
  
2. En el menú **Archivo**, elija **Nuevo** y después seleccione **Proyecto**.  
  
     Aparece el cuadro de diálogo **Nuevo proyecto** .  
  
3. Seleccione el **.NET Framework 3.0** opción o el **.NET Framework 3.5** opción en la lista desplegable situada en la parte superior de la **nuevo proyecto** ventana para tener acceso al diseñador heredado.  
  
    > [!NOTE]
    > La opción predeterminada de [!INCLUDE[vs2010](../includes/vs2010-md.md)] es **.NET Framework 4**. Esta opción se usa para crear aplicaciones [!INCLUDE[wf](../includes/wf-md.md)] que tienen como destino [!INCLUDE[netfx40_short](../includes/netfx40-short-md.md)] y no usa el diseñador heredado.  
  
4. En el **tipos de proyecto** panel, seleccione Visual C# o Visual Basic (en **otros lenguajes**) y, a continuación, seleccione **flujo de trabajo**.  
  
5. En el **plantillas** panel, seleccione **biblioteca de flujo de trabajo secuencial**.  
  
6. En el **nombre** , escriba un nombre descriptivo para el proyecto para que sea fácil de identificar.  
  
7. En el **ubicación** cuadro, escriba el directorio en el que desea guardar el proyecto o haga clic en **examinar** para desplazarse hasta él.  
  
     Si desea que un directorio de soluciones creado para el proyecto, seleccione el **crear directorio para la solución** casilla de verificación y escriba un nombre en el **nombre de la solución** cuadro.  
  
8. Haga clic en **Aceptar**.  
  
## <a name="see-also"></a>Vea también  
 [Crear proyectos de flujo de trabajo heredados](../workflow-designer/creating-legacy-workflow-projects.md)   
 [Estilos de creación de flujo de trabajo](https://msdn.microsoft.com/aacf4ec6-da05-4974-958a-974769dda739)