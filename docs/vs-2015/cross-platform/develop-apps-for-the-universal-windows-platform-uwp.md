---
title: Desarrollar aplicaciones para la Plataforma universal de Windows (UWP) | Microsoft Docs
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- tgt-pltfrm-cross-plat
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eac59cb6-f12e-4a77-9953-6d62b164a643
caps.latest.revision: 50
author: gewarren
ms.author: gewarren
manager: wpickett
ms.openlocfilehash: 24dfca5d4ac8432cbe659bb42ca54d0398c47c04
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/16/2018
ms.locfileid: "51766472"
---
# <a name="develop-apps-for-the-universal-windows-platform-uwp"></a>Desarrollar aplicaciones para la Plataforma universal de Windows (UWP)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Con la Plataforma universal de Windows y nuestro núcleo de Windows, puede ejecutar la misma aplicación de Windows 10 en cualquier dispositivo, desde teléfonos a equipos de escritorio. Cree estas aplicaciones con Visual Studio 2015 y las herramientas de desarrollo de aplicaciones Windows universales.  
  
 ![Plataforma universal de Windows](../cross-platform/media/uwp-coreextensions.png "UWP_CoreExtensions")  
  
 Ejecute su aplicación en un teléfono con Windows 10, un equipo de escritorio con Windows 10 o una Xbox. Es el mismo paquete de aplicaciones. Con la introducción del núcleo unificado de Windows 10, un mismo paquete de la aplicación puede ejecutarse en todas las plataformas. Varias plataformas tienen SDK de extensión que puede agregar a su aplicación para aprovechar los comportamientos específicos de cada plataforma. Por ejemplo, un SDK de extensión para móvil controla la pulsación del botón atrás en un teléfono Windows. Si hace referencia a un SDK de extensión en su proyecto, solo tiene que agregar comprobaciones en tiempo de ejecución para comprobar que ese SDK se encuentre disponible en esa plataforma. Así es cómo puede tener el mismo paquete de aplicaciones para todas las plataformas.  
  
 **¿Qué es el núcleo de Windows?**  
  
 Por primera vez Windows se ha refactorizado para que tenga un núcleo común para todas las plataformas Windows 10. Hay un código fuente común, un kernel de Windows común, una pila común de E/S de archivos y un modelo de aplicación común. Para la interfaz de usuario, solo hay un marco de interfaz de usuario XAML y un marco de interfaz de usuario HTML. De este modo puede concentrarse en la creación una excelente aplicación, ya que hemos hecho muy fácil que pueda ejecutarse en distintos dispositivos con Windows 10.  
  
 **¿Qué es exactamente la Plataforma universal de Windows?**  
  
 Sencillamente es una colección de contratos y versiones. Estos le permiten definir dónde se puede ejecutar la aplicación. Ya no se establece un sistema operativo como destino. Ahora el destino de la aplicación son una o varias familias de dispositivos. Obtenga información más detallada de esta [Guía de la plataforma](http://msdn.microsoft.com/library/windows/apps/dn894631.aspx).  
  
## <a name="requirements"></a>Requisitos  
 Las herramientas de desarrollo de aplicaciones Windows universales incluyen emuladores que puede usar para ver el aspecto de la aplicación en diferentes dispositivos. Si quiere usar estos emuladores, debe instalar este software en un equipo físico. El equipo físico debe ejecutar Windows 8.1 (x 64) Professional Edition o superior y disponer de un procesador compatible con Cliente Hyper-V y Traducción de direcciones de segundo nivel (SLAT). Los emuladores no se pueden usar cuando Visual Studio está instalado en una máquina virtual.  
  
 Esta es la lista del software que necesita:  
  
- [Windows 10](http://windows.microsoft.com/windows/downloads)  
  
- [Visual Studio 2015](http://go.microsoft.com/fwlink/p/?LinkId=526725). Asegúrese de que las Herramientas de desarrollo de aplicaciones de Windows universales estén seleccionadas en la lista de características opcionales. Sin estas herramientas no podrá crear aplicaciones universales.  
  
  Después de instalar este software, necesitará [Habilitar el dispositivo Windows 10](https://msdn.microsoft.com/library/windows/apps/xaml/dn706236.aspx) para el desarrollo. (Ya no necesita una licencia de desarrollador para cada dispositivo Windows 10).  
  
  **Compatibilidad de Windows 8.1 y Windows 7**  
  
  Si decide desarrollar aplicaciones Windows universales con Visual Studio de 2015 en una plataforma distinta de Windows 10, estas son las restricciones:  
  
- Windows 8.1: no puede ejecutar la aplicación localmente (solo en un dispositivo remoto de Windows 10). Puede utilizar los emuladores de Visual Studio, pero no el simulador.  
  
- Windows 7: no puede ejecutar la aplicación localmente (solo en un dispositivo remoto de Windows 10). No puede utilizar ni los emuladores ni el simulador de Visual Studio.  
  
  Solo puede utilizar el Diseñador XAML si la plataforma de desarrollo es Windows 10.  
  
## <a name="universal-windows-apps"></a>Aplicaciones Windows universales  
 Elija su lenguaje de desarrollo preferido (C#, Visual Basic, C++ o JavaScript) para [crear una aplicación universal de Windows para dispositivos Windows 10](http://msdn.microsoft.com/library/windows/apps/xaml/dn609832.aspx#target_win10). O bien, vea este [vídeo de introducción](http://channel9.msdn.com/Series/ConnectOn-Demand/229).  
  
 Si tiene aplicaciones de la Tienda Windows 8.1, de Windows Phone 8.1 o aplicaciones universales de Windows creadas con Visual Studio 2015 RC, [migre estas aplicaciones](http://msdn.microsoft.com/library/windows/apps/xaml/mt238321.aspx) para usar la Plataforma universal de Windows más reciente.  
  
 Después de crear la aplicación Windows universal, debe [empaquetarla](https://msdn.microsoft.com/library/windows/apps/hh454036.aspx) para instalarlo en un dispositivo Windows 10 o enviarla a la Tienda Windows.

