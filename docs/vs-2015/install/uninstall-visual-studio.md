---
title: Desinstalar Visual Studio | Documentos de Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- uninstalling
- uninstalling visual studio
- uninstall
- uninstall Visual Studio
ms.assetid: 0e445255-b796-426d-ad93-a4d8e36da2c5
caps.latest.revision: 9
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.openlocfilehash: 25fbfec12299cecf265437baa04a3dd86093f30b
ms.sourcegitcommit: 9ceaf69568d61023868ced59108ae4dd46f720ab
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/12/2018
ms.locfileid: "49259348"
---
# <a name="uninstall-visual-studio"></a>Desinstalar Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Para obtener la documentación más reciente de Visual Studio 2017, consulte [desinstalar Visual Studio 2017](https://docs.microsoft.com/visualstudio/install/uninstall-visual-studio).

Esta página le guiará en el proceso de desinstalación de Visual Studio 2015, una versión anterior de nuestro conjunto integrado de herramientas de productividad para desarrolladores.  
  
##  <a name="uninstalling"></a>   
#### <a name="to-uninstall-visual-studio-by-using-the-standard-uninstallation-method"></a>Para desinstalar Visual Studio mediante el método de desinstalación "estándar"  
  
1.  En **Panel de Control**, en el **programas y características** página, elija la edición del producto que desea desinstalar y, a continuación, elija **cambio**.  
  
2.  En el Asistente para la instalación, elija **desinstalar**, elija **Sí**y, a continuación, siga las instrucciones restantes del asistente.  
  
 Este método estándar o predeterminado omitirá algunos elementos que la primera instalación de Visual Studio que se instalaron (por ejemplo, el Microsoft .NET Framework, Microsoft Visual C++ Redistributable, Microsoft SQL Server, etcetera.).   Estos elementos se dejan instalados porque muchas otras aplicaciones que dependen de ellos. Sin embargo, si desea quitarlos, selecciónelos en **programas y características**y, a continuación, quite cada uno individualmente.  
  
#### <a name="to-uninstall-visual-studio-and-all-other-related-files-that-is-to-uninstall-almost-everything"></a>Para desinstalar Visual Studio y otros archivos relacionados (es decir, desinstalarlo casi todo)  
  
1.  Busque el archivo .exe de Visual Studio (por ejemplo, busque "vs_enterprise.exe").  
  
    > [!NOTE]
    >  El archivo debe estar en una subcarpeta de "%ProgramData%\Package Cache", por ejemplo: caché C:\ProgramData\Package\\\vs_enterprise.exe {37e19555-e88d-4aed-9d42-82d0784d2b79}  
  
2.  Ejecute el archivo .exe mediante el uso de la desinstalación o forzar los parámetros de línea de comandos.  
  
     Por ejemplo, ejecute ```vs_enterprise.exe /uninstall /force```, que quitará en una desinstalación predeterminada Visual Studio y la mayoría de los componentes principales que se omiten. Sin embargo, no se quitará todo el contenido adicional que los complementos de Visual Studio y pueden instalar extensiones (por ejemplo, actualizaciones de Visual Studio y otros componentes opcionales).  
  
    > [!TIP]
    > Como alternativa, puede usar el "**Total Uninstaller**" herramienta para quitar todo lo que Visual Studio o puede que haya instalado las actualizaciones de Visual Studio. Es decir, cualquier versión de Visual Studio 2013 o posterior. Para obtener más información, consulte el [herramienta de Visual Studio Uninstaller](https://github.com/Microsoft/VisualStudioUninstaller/releases) en GitHub.  
  
#### <a name="to-uninstall-visual-studio-in-silent-or-passive-modes-that-is-to-uninstall-from-source"></a>Para desinstalar Visual Studio en los modos silencioso o pasivos (es decir, para desinstalar desde el origen)  
  
1.  En el equipo donde está instalado Visual Studio, abra el símbolo del sistema de Windows.  
  
2.  Escriba los parámetros siguientes:  
  
     *DVDRoot* \\< archivo de instalación\> \</quiet&#124;/passive > [/norestart] /Uninstall  
  
#### <a name="to-roll-back-to-a-previous-version-or-release-of--visual-studio"></a>Para revertir a una versión anterior o una versión de Visual Studio  
  
1.  Desinstalar Visual Studio con cualquiera de los métodos descritos en este tema.  
  
    > [!WARNING]
    >  Desinstalar una versión actual de Visual Studio (o una actualización de Visual Studio) y, a continuación, instalar una versión anterior podrían no funcionar según lo previsto.  
    >   
    >  El resultado depende de qué versión de Visual Studio instalado, se instalan las versiones de sus componentes, qué productos instalados que pueden tener dependencias ya sea la versión de Visual Studio o sus componentes, y por último, en la versión anterior de Visual Studio va a instalar o reinstalar.  Debido a todas estas variables, una desinstalación estándar a menudo le componentes dejar detrás de que no funcionen con las versiones o versiones anteriores de Visual Studio.  
    >   
    >  Por lo tanto, para obtener mejores resultados, se recomienda usar la [herramienta de Visual Studio Uninstaller](https://github.com/Microsoft/VisualStudioUninstaller/releases).  
  
2.  Instalar o reinstalar la versión anterior de Visual Studio que desea usar.  
  
 Incluso si instala una versión anterior de Visual Studio, el programa de instalación todavía es posible que intente usar una versión más reciente o si está disponible. Para obtener más información, consulte el [Cómo: instalar una versión específica de Visual Studio](../install/how-to-install-a-specific-release-of-visual-studio.md) tema.  
  
## <a name="see-also"></a>Vea también  
 [Instalar Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx)