---
title: 'Cómo: depurar código fuente de .NET Framework | Documentos de Microsoft'
ms.custom: ''
ms.date: 02/23/2018
ms.technology: vs-ide-debug
ms.topic: conceptual
helpviewer_keywords:
- debugging, .NET Framework source
ms.assetid: fc12e472-ac6a-4e77-8e22-a769e13a03b8
author: mikejo5000
ms.author: mikejo
manager: douge
ms.workload:
- dotnet
ms.openlocfilehash: 8377ed73479441272b2f1910767fa7e2a4ff0196
ms.sourcegitcommit: 3d10b93eb5b326639f3e5c19b9e6a8d1ba078de1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2018
---
# <a name="how-to-debug-net-framework-source"></a>Cómo: Depurar código fuente de .NET Framework
Para depurar código fuente de .NET Framework, debe tener acceso a los símbolos de depuración para el código. También debe habilitar la ejecución paso a paso en código fuente de .NET Framework.  
  
 Puede habilitar .NET Framework paso a paso y símbolo de cómo descargar el **opciones** cuadro de diálogo. Al habilitar la descarga de símbolos, puede descargarlos inmediatamente o habilitar la opción para una descarga posterior. Si no los descarga inmediatamente, los símbolos se descargarán la próxima vez que inicie la depuración de la aplicación. También puede hacer una descarga manual de la **módulos** ventana o el **pila de llamadas** ventana.  
  
### <a name="to-enable-net-framework-source-debugging"></a>Para habilitar la depuración de código fuente de .NET Framework  
  
1.  En el **herramientas** menú, haga clic en **opción**s.  
  
2.  En el **opciones** cuadro de diálogo, haga clic en el **depuración** categoría.  
  
3.  En el **General** , configure **origen de .NET Framework de habilitar ejecución paso a paso.**  
  
    1.  Si tenía habilitada la opción Sólo mi código , un cuadro de diálogo de advertencia le indicará que dicha opción se ha deshabilitado. Haga clic en **Aceptar**.  
  
    2.  Si no tenía una ubicación de caché de símbolos establecida, otro cuadro de diálogo de advertencia le indicará que se ha establecido una ubicación de caché de símbolos predeterminada. Haga clic en **Aceptar**.  
  
4.  En el **depuración** categoría, haga clic en **símbolos**.  
  
5.  Si desea cambiar la ubicación de caché de símbolos, modifique la ubicación en **almacenar en caché los símbolos de este directorio** o haga clic en **examinar** para elegir una ubicación.  
  
6.  Si desea descargar inmediatamente los símbolos, haga clic en **cargar símbolos utilizando ubicaciones indicadas**.  
  
     Este botón no está disponible en modo de diseño, pero está disponible durante la depuración.  
  
     Si decide no descargar ahora los símbolos, estos se descargarán automáticamente la próxima vez que inicie la depuración del programa.  
  
7.  Haga clic en **Aceptar** para cerrar el cuadro de diálogo **Opciones**.  
  
### <a name="to-load-framework-symbols-using-the-modules-window"></a>Para cargar símbolos de Framework mediante la ventana Módulos  
  
1.  En el **módulos** ventana (durante la depuración, elija **depurar** > **Windows** > **módulos**), Haga clic en un módulo para el que no están cargados los símbolos. Puede indicar si se cargan los símbolos o no examinando el **estado símbolos** columna.  
  
2.  Seleccione **configuración de símbolos** y haga clic en **servidores de símbolos de Microsoft** para descargar los símbolos desde el servidor de símbolos públicos de Microsoft. O bien, puede haga clic en el módulo y elija **cargar símbolos** a cargarlos desde un directorio donde se haya almacenado previamente los símbolos.  
  
### <a name="to-load-framework-symbols-using-the-call-stack-window"></a>Para cargar símbolos de Framework mediante la ventana Pila de llamadas  
  
1.  En el **pila de llamadas** ventana, haga un marco para el que no están cargados los símbolos. Este marco se oscurecerá.  
  
2.  Seleccione **configuración de símbolos** y haga clic en **servidores de símbolos de Microsoft**, o haga clic en el módulo y elija **ruta de acceso de símbolos**.  
  
## <a name="see-also"></a>Vea también  
 [Depurar código administrado](../debugger/debugging-managed-code.md)   
 [Especificar los símbolos (.pdb) y archivos de código fuente](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)