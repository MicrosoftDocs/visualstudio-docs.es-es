---
title: "Instalación de Visual Studio 2017 | Microsoft Docs"
description: "Obtenga información sobre cómo instalar Visual Studio, paso a paso."
ms.custom: 
ms.date: 05/16/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio
- dev15
- set up Visual Studio
- Visual Studio setup
- Visual Studio installer
ms.assetid: 8d4297e4-9f43-4f12-95ec-22e61154480e
author: TerryGLee
ms.author: tglee
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 9713f09b7379b14b9362e3853a910948935c501e
ms.openlocfilehash: 9f7c1d33191adf3fb54cf59cd98ae5fffe14eee4
ms.contentlocale: es-es
ms.lasthandoff: 05/31/2017

---
# <a name="install-visual-studio-2017"></a>Instalación de Visual Studio 2017
Le presentamos una nueva manera de instalar Visual Studio. En nuestra última versión, hemos facilitado la selección e instalación de las características que necesita, y hemos reducido el espacio mínimo de Visual Studio para que instale más rápidamente y con menor impacto en el sistema que antes.

¿Quiere saber más sobre otras novedades? Vea nuestras [notas de la versión](https://www.visualstudio.com/news/releasenotes/vs2017-relnotes). Y para obtener información más detallada sobre cómo hemos rediseñado la experiencia de instalación, vea nuestras publicaciones del blog "[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)" (Instalador de Visual Studio más rápido y eficaz) y "[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)" (Anatomía de la instalación de bajo impacto de Visual Studio).  

¿Está listo para instalarlo? Le guiaremos paso a paso.

## <a name="check-system-requirements"></a>Comprobar los requisitos del sistema
Antes de comenzar, compruebe los [requisitos del sistema](https://www.visualstudio.com/productinfo/vs2017-system-requirements-vs) para asegurarse de que su equipo está listo para instalar Visual Studio 2017.

## <a name="download-visual-studio"></a>Descargue Visual Studio
Para comenzar, querrá descargar Visual Studio. Para hacerlo, haga clic en el botón siguiente, haga clic en **Guardar** y, después, haga clic en **Abrir carpeta**.

 > [!div class="button"]
 > [Descargar Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

## <a name="install-the-installer"></a>Instalar el instalador  
Cuando descargue Visual Studio 2017, obtendrá un archivo de programa previo que a su vez instala nuestro nuevo instalador ligero. Este nuevo instalador incluye todo lo que necesita para personalizar su instalación.  

> [!IMPORTANT]
> Si tiene instalada una versión preliminar de Visual Studio 2017 en el equipo, se le pedirá que la quite antes de instalar Visual Studio 2017.

1.  Desde la carpeta **Descargas**, haga doble clic en el archivo de arranque que coincide o es similar a uno de los siguientes:

  * **vs_enterprise.exe** para Visual Studio Enterprise
  * **vs_professional.exe** para Visual Studio Professional
  * **vs_community.exe** para Visual Studio Community  <br><br>

  Si recibe un aviso de Control de cuentas de usuario, haga clic en **Sí**.  

2.  Le pediremos que acepte los [Términos de licencia](https://www.visualstudio.com/license-terms/) de Microsoft y la [Declaración de privacidad](https://go.microsoft.com/fwlink/?LinkID=824704) de Microsoft. Haga clic en **Continuar**.  

   ![Términos de licencia y declaración de privacidad](~/docs/install/media/vs2017-privacy-and-license-terms.PNG "Términos de licencia y declaración de privacidad de Microsoft")  

Verá varias pantallas de estado que muestran el progreso de la instalación. Después de que el instalador termine la instalación, es el momento de seleccionar los conjuntos de características o las cargas de trabajo.

## <a name="install-workloads"></a>Instalar cargas de trabajo  
 Puede personalizar su instalación con cargas de trabajo. Seleccione una o varias cargas de trabajo; cada una contiene las características que necesita para el lenguaje de programación o la plataforma que prefiera.  

 A continuación se indica cómo obtenerlas.  

1.  Busque la carga de trabajo que quiera en la pantalla **Instalando Visual Studio**.  

  ![Cuadro de diálogo de instalación de Visual Studio 2017](~/docs/install/media/vs2017-workloads.PNG "Instalación de cargas de trabajo de Visual Studio")

     Por ejemplo, elija la carga de trabajo de desarrollo de escritorio de .NET. Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.  

2.  Después de que seleccione las cargas de trabajo que quiera, haga clic en **Instalar**.  

    Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

3.  Después de que se instalen los nuevos componentes y cargas de trabajo, haga clic en **Iniciar**.

## <a name="install-individual-components"></a>Instalar componentes individuales

Si no quiere usar la característica útil de cargas de trabajo para personalizar la instalación de Visual Studio, haga clic en la opción **Componentes individuales** desde el instalador de Visual Studio, seleccione lo que quiera y, después, siga las indicaciones.

  ![Visual Studio 2017 - Instalar componentes individuales](~/docs/install/media/vs2017-components.PNG "Instalar componentes individuales de Visual Studio")

## <a name="install-language-packs"></a>Instalar paquetes de idioma

Para instalar Visual Studio 2017 en un idioma de su elección, haga clic en la opción **Paquetes de idioma** del instalador de Visual Studio y siga las indicaciones.

  ![Visual Studio 2017 - Instalar paquetes de idioma](~/docs/install/media/vs2017-languages.PNG "Instalar paquetes de idioma de Visual Studio")

### <a name="change-the-installer-language"></a>Cambiar el idioma del instalador

De manera predeterminada, el programa instalador intenta hacer coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. El instalador recuerda esta configuración. Puede cambiar esta configuración ejecutando el instalador desde la línea de comandos. Por ejemplo, puede forzar al instalador a utilizar el inglés utilizando el comando siguiente: `vs_installer.exe --locale en-US`. El instalador recordará esta configuración cuando se ejecute la próxima vez. El instalador admite los siguientes tokens de idioma: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES y tr-TR.

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, vea sugerencias para la solución de problemas en la página [Solucionar problemas de errores de instalación y actualización de Visual Studio 2017](troubleshooting-installation-issues.md).

## <a name="see-also"></a>Vea también  
* [Modificación de Visual Studio 2017](modify-visual-studio.md)
* [Actualizar Visual Studio 2017](update-visual-studio.md)
* [Desinstalación de Visual Studio 2017](uninstall-visual-studio.md)
* [Guía del administrador de Visual Studio 2017](visual-studio-administrator-guide.md)
* [Cómo notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)

