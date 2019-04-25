---
title: Solución de problemas y problemas conocidos (Visual Studio Tools para Unity) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-unity-tools
ms.topic: troubleshooting
ms.assetid: 8f5db192-8d78-4627-bd07-dbbc803ac554
caps.latest.revision: 7
author: conceptdev
ms.author: crdun
manager: jillfra
ms.openlocfilehash: 6e1b34cbc2497bd70f65021c83db4f59480519f1
ms.sourcegitcommit: 1fc6ee928733e61a1f42782f832ead9f7946d00c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60095963"
---
# <a name="troubleshooting-and-known-issues-visual-studio-tools-for-unity"></a>Solución de problemas y problemas conocidos (Visual Studio Tools para Unity)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

En esta sección encontrará soluciones a problemas comunes con Visual Studio Tools para Unity y descripciones de problemas conocidos. Asimismo descubrirá cómo puede ayudar a mejorar Visual Studio Tools para Unity mediante la notificación de errores.  
  
## <a name="troubleshooting"></a>Solución de problemas  
 Para resolver algunos problemas comunes que se producen al trabajar con Visual Studio Tools para Unity, consulte las secciones siguientes.  
  
### <a name="migrating-from-unityvs-to-visual-studio-tools-for-unity"></a>Migrar de UnityVS a Visual Studio Tools para Unity  
 Si está migrando de UnityVS a Visual Studio Tools para Unity, debe generar nuevas soluciones de Visual Studio para los proyectos de Unity.  
  
##### <a name="to-migrate-your-unity-project-from-unityvs-18-to-visual-studio-tools-for-unity-19"></a>Migrar un proyecto Unity de UnityVS 1.8 a Visual Studio Tools para Unity 1.9  
  
1. Elimine los antiguos archivos de solución y proyecto del proyecto de Unity. En el directorio raíz del proyecto Unity, busque los archivos .sln y .*proj de Visual Studio y elimínelos todos.  
  
2. Importe el paquete de Visual Studio Tools para Unity en su proyecto de Unity. Para obtener información sobre cómo importar el paquete de VSTU, vea Configurar Visual Studio Tools para Unity en la página [Introducción](../cross-platform/getting-started-with-visual-studio-tools-for-unity.md) .  
  
3. Genere los nuevos archivos de solución y proyecto. Si quiere generarlos ahora, en el menú principal del Editor de Unity, elija **Visual Studio Tools**, **Generar archivos de proyecto**. De lo contrario, puede omitir este paso si lo desea; Visual Studio Tools para Unity generará los nuevos archivos automáticamente al elegir **Visual Studio Tools**, **Abrir en Visual Studio**.  
  
### <a name="visual-studio-wont-load-the-solution-that-visual-studio-tools-for-unity-created"></a>Visual Studio no cargará la solución que creó Visual Studio Tools para Unity  
 Para obtener más información, consulte [la respuesta a esta cuestión de StackOverFlow](http://stackoverflow.com/a/24035907/36702).  
  
### <a name="on-windows-8-visual-studio-asks-to-download-the-unity-target-framework"></a>En Windows 8, Visual Studio le pide que descargue el marco de destino de Unity  
 UnityVS necesita .NET Framework 3.5, que no instala de manera predeterminada en Windows 8. Para corregir este problema, siga las instrucciones para descargar e instalar .NET Framework 3.5.  
  
## <a name="known-issues"></a>Problemas conocidos  
 Existen problemas conocidos en Visual Studio Tools para Unity que se deben a cómo interactúa el depurador con la antigua versión de Unity del compilador de C#. Estamos trabajando para ayudar a solucionar estos problemas, pero mientras tanto podría experimentar los siguientes problemas.  
  
- A veces, al depurar, Unity se bloquea.  
  
- A veces, al depurar, Unity se inmoviliza.  
  
- Al entrar y salir de métodos a veces se produce un comportamiento incorrecto, especialmente en iteradores o dentro de instrucciones switch.  
  
## <a name="reporting-errors"></a>Notificar errores  
 Ayúdenos a mejorar la calidad de Visual Studio Tools para Unity mediante el envío de informes de errores cuando experimente bloqueos, inmovilizaciones u otro tipo de errores. Esto nos ayudará a investigar y solucionar problemas en Visual Studio Tools para Unity. ¡Gracias!  
  
### <a name="how-to-report-an-error-when-visual-studio-freezes"></a>Cómo informar de un error cuando Visual Studio se inmoviliza  
 Hay informes que indican que a veces Visual Studio se inmoviliza al depurar con Visual Studio Tools para Unity, pero necesitamos más datos para comprender este problema. Puede ayudarnos a investigarlo siguiendo los pasos indicados a continuación.  
  
##### <a name="to-report-that-visual-studio-freezes-while-debugging-with-visual-studio-tools-for-unity"></a>Para informar de que Visual Studio se inmoviliza durante la depuración con Visual Studio Tools para Unity  
  
1. Abra una nueva instancia de Visual Studio.  
  
2. Abra el diálogo Asociar al proceso. En la nueva instancia de Visual Studio, en el menú principal, elija **Depurar**, **Asociar al proceso**.  
  
3. Asocie el depurador a la instancia inmovilizada de Visual Studio. En el diálogo **Asociar al proceso** , seleccione la instancia inmovilizada de Visual Studio en la tabla **Procesos disponibles** y, a continuación, elija el botón **Asociar** .  
  
4. Pause el Depurador. En el menú principal de la nueva instancia de Visual Studio elija **Depurar**, **Interrumpir todo** o simplemente presione las teclas **Ctrl+Alt+Interrumpir**.  
  
5. Cree un volcado del subproceso. En la ventana Comandos, escriba el siguiente comando y presione **ENTRAR**.  
  
   ```powershell  
   Debug.ListCallStack /AllThreads /ShowExternalCode  
   ```  
  
    Puede que primero tenga que hacer visible la ventana **Comando** . En el menú principal de Visual Studio elija **Vista**, **Otras ventanas**, **Ventana Comandos**.  
  
6. Por último, envíe el volcado del subproceso a [vstusp@microsoft.com](mailto:vstusp@microsoft.com), junto con una descripción de lo que estaba haciendo cuando Visual Studio se quedó inmovilizado.
