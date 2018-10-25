---
title: 'Cómo: depurar con código fuente de Code Center Premium | Microsoft Docs'
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-debug
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- FSharp
- VB
- CSharp
- C++
helpviewer_keywords:
- Code Center Premium
- debugging [Visual Studio], Code Center Premium
ms.assetid: 18b4769d-b007-4428-9dae-9e72c283ff0d
caps.latest.revision: 26
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5ac76a294c8f6b536da93f06afe6e423ca593b84
ms.sourcegitcommit: 240c8b34e80952d00e90c52dcb1a077b9aff47f6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/23/2018
ms.locfileid: "49824170"
---
# <a name="how-to-debug-with-code-center-premium-source"></a>Cómo: Depurar código fuente con Code Center Premium
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Con el depurador de [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], puede depurar código fuente compartido seguro de Microsoft MSDN Code Center Premium.  
  
 En este tema se explica cómo configurar y depurar el código fuente de Code Center Premium en Visual Studio.  
  
### <a name="to-prepare-for-debugging-with-code-center-premium"></a>Para preparar la depuración con Code Center Premium  
  
1. Conecte el lector de SmartCard e inserte la tarjeta que obtuvo en la Iniciativa de código fuente compartido.  
  
2. Inicie Visual Studio.  
  
3. En el menú **Herramientas** , haga clic en **Opciones**.  
  
4. En el **opciones** cuadro de diálogo, abra el **depuración** nodo y haga clic en **General**.  
  
5. Desactive el **habilitar solo mi código (solo administrado)** casilla de verificación.  
  
6. Seleccione **Habilitar compatibilidad de servidor de origen**.  
  
7. Borrar **requieren archivos de origen para ajustarse exactamente a la versión original**.  
  
8. En el **depuración** nodo, haga clic en **símbolos**.  
  
9. En el **archivo de símbolos (.pdb) ubicaciones** cuadro, desactive la **servidores de símbolos de Microsoft** casilla de verificación y agregue las siguientes ubicaciones:  
  
     `https://codepremium.msdn.microsoft.com/symbols`  
  
     `src=https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  No olvide incluir la barra diagonal final<strong>/</strong> al final de la ruta de acceso.  
  
     Mueva estas ubicaciones a la parte superior de la lista para asegurarse de que estos símbolos se cargan en primer lugar.  
  
   > [!NOTE]
   >  Estas ubicaciones de Code Center Premium deben enumerarse primero de modo que sean las primeras ubicaciones que se cargan. En Visual Studio 2010, no se puede mover ningún servidor situado encima del **servidores de símbolos de Microsoft** entrada, lo que debe desactivar la casilla de verificación.  
   > 
   >  Para cargar símbolos de Microsoft durante una sesión de depuración, haga lo siguiente:  
   > 
   > 1. En el **depurar** menú, elija **Windows** y, a continuación, elija **módulos**.  
   >    2.  Seleccione el módulo del que desee símbolos y, a continuación, abra el menú contextual. Elija **cargar símbolos desde** y, a continuación, elija **servidores de símbolos de Microsoft**.  
  
10. En el **almacenar en caché los símbolos de los servidores de símbolos en este directorio** cuadro, escriba una ubicación como `C:\symbols` donde Code Center Premium puede almacenar en caché los símbolos. Almacenar en caché los símbolos puede mejorar significativamente el rendimiento durante la depuración.  
  
     Si tiene dificultades para depurar el código fuente con [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] después de completar este procedimiento, compruebe la ubicación de los archivos almacenados en caché previamente y los archivos de símbolos anticuados. Quite los archivos de símbolos anticuados.  
  
11. Haga clic en **Aceptar**.  
  
12. Reinicie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] para asegurarse de que se conserva la configuración.  
  
### <a name="to-debug-your-source-code-using-attach-to-process"></a>Para depurar el código fuente utilizando Asociar al proceso  
  
1.  Conecte el lector de SmartCard e inserte la tarjeta que obtuvo en la Iniciativa de código fuente compartido.  
  
2.  Inicie Visual Studio.  
  
3.  Abra el proyecto de Visual Studio.  
  
4.  En el **herramientas** menú, haga clic en **asociar al proceso**.  
  
5.  En el **asociar al proceso** cuadro de diálogo, haga clic en **seleccione**.  
  
6.  En el **Seleccionar tipo de código** cuadro de diálogo **detectar estos tipos de código**, seleccione **nativo**, **administrada**, y **administrados () v4.0)**.  
  
7.  Haga clic en **Aceptar** para descartar el **Seleccionar tipo de código** cuadro de diálogo.  
  
8.  En el **procesos disponibles** , seleccione el proceso que desea depurar.  
  
9. Haga clic en **Adjuntar**.  
  
10. Cuando se le pida que confirme el certificado, haga clic en **Aceptar**. A continuación, escriba su PIN. Acepte los términos de uso de Code Center Premium, si se lo piden.  
  
     Descargar los símbolos puede tardar mucho tiempo, dependiendo de la velocidad de la red. La barra de estado indicará cuando se han descargado correctamente todos los símbolos.  
  
11. Repita los pasos de Asociar al proceso para todos los proyectos administrados de la solución.  
  
### <a name="to-debug-source-code-from-an-existing-solution"></a>Para depurar el código fuente de una solución existente  
  
1. En **el Explorador de soluciones**, abra el menú contextual de la solución y, a continuación, elija **propiedades**.  
  
2. En el cuadro de diálogo páginas de propiedades de la solución, elija **depurar archivos de código fuente** en el **propiedades comunes** nodo.  
  
3. Agregue la siguiente ubicación a la **directorios que contienen archivos de código fuente** lista:  
  
    `https://codepremium.msdn.microsoft.com/source/Visual%20Studio%202010/SP1/`  
  
   > [!NOTE]
   >  No olvide incluir la barra diagonal final<strong>/</strong> al final de la ruta de acceso.  
  
4. Para cada proyecto administrado de la solución, haga lo siguiente  
  
   1.  En el Explorador de soluciones, abra el menú contextual para el proyecto y, a continuación, elija **propiedades**.  
  
   2.  Seleccione **depurar** y, a continuación, elija **Habilitar depuración de código no administrado**.  
  
### <a name="to-debug-your-solution-with-code-center-premium-source"></a>Para depurar la solución con el código fuente de Code Center Premium  
  
1.  En la clase `Package`, establezca un punto de interrupción en el constructor del paquete.  
  
2.  En el `Debug` menú, haga clic en **Iniciar depuración**.  
  
3.  Cuando se alcance el punto de interrupción en el constructor del paquete, vaya a la **pila de llamadas** ventana y haga clic con el marco de pila del ensamblado que desea cargar símbolos y, a continuación, **cargar símbolos**.  
  
     Haga doble clic en el marco de la llamada para cargar el código fuente.  
  
### <a name="to-browse-source-code-on-code-center-premium"></a>Para examinar el código fuente en Code Center Premium  
  
1.  Conecte el lector de SmartCard e inserte la tarjeta que obtuvo en la Iniciativa de código fuente compartido.  
  
2.  Inicie Internet Explorer y escriba la siguiente dirección URL: `https://codepremium.msdn.microsoft.com`  
  
3.  Busque el código fuente que desea.  
  
## <a name="see-also"></a>Vea también  
 [Preparación y configuración de la depuración](../debugger/debugger-settings-and-preparation.md)   
 [Seguridad del depurador](../debugger/debugger-security.md)   
 [Code Center Premium](http://www.microsoft.com/resources/sharedsource/ccp.mspx)



