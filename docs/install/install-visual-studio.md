---
title: Instalar Visual Studio 2017 RC | Microsoft Docs
description: "Obtenga información sobre cómo instalar Visual Studio, paso a paso."
ms.custom: 
ms.date: 11/18/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: get-started-article
f1_keywords:
- vs.about
helpviewer_keywords:
- install Visual Studio Preview
- install Visual Studio
- installing Visual Studio
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
translationtype: Human Translation
ms.sourcegitcommit: 5e1ab0284a11fb9ecf30694d22b8bb5dc7a52a6d
ms.openlocfilehash: 997a1e0966c5e08314c616dba76842120ab50d63

---
# <a name="install-visual-studio-2017-rc"></a>Instalar Visual Studio 2017 RC
Le presentamos una nueva manera de instalar Visual Studio. En nuestra última versión, hemos facilitado la selección e instalación de las características que necesita, y hemos reducido el espacio mínimo de Visual Studio para que instale más rápidamente y con menor impacto en el sistema que antes.  

 ¿Quiere saber más sobre otras novedades de RC? Vea nuestras [notas de la versión](https://www.visualstudio.com/news/releasenotes/vs15-relnotes). Y para obtener información más detallada sobre cómo hemos rediseñado la experiencia de instalación, vea nuestras publicaciones del blog "[Faster and leaner Visual Studio installer](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer/)" (Instalador de Visual Studio más rápido y eficaz) y "[Anatomy of a low-impact Visual Studio installation](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install/)" (Anatomía de la instalación de bajo impacto de Visual Studio).  

 ¿Está listo para instalarlo? Le guiaremos paso a paso. Comencemos.  

## <a name="install-the-installer"></a>Instalar el instalador  
 Cuando descargue Visual Studio 2017 RC, obtendrá un archivo de programa previo que a su vez instala nuestro nuevo instalador ligero. Este nuevo instalador incluye todo lo que necesita para personalizar su instalación.  

> [!IMPORTANT]
> Si tiene instalada una versión preliminar de Visual Studio 2017 en el equipo, se le pedirá quitarla antes de instalar Visual Studio 2017 RC.

1.  [Descargue Visual Studio Enterprise 2017 RC](https://www.visualstudio.com/vs/visual-studio-2017-rc/) y haga clic en **Guardar**.  Después, desde la carpeta **Descargas**, ejecute el archivo `vs_Enterprise.exe`.  

     Si recibe un aviso de Control de cuentas de usuario, haga clic en **Sí**.  

2.  Le pediremos que acepte los [Términos de licencia](https://www.visualstudio.com/support/legal/mt591984) de Microsoft y la [Declaración de privacidad](https://www.visualstudio.com/dn948229) de Microsoft. Haga clic en **Instalar** para continuar.  

  ![Términos de licencia y declaración de privacidad](media/01-installingdev15prev4-licensetermsandprivacystatement.png "Términos de licencia y declaración de privacidad de Microsoft")  

3.  Verá varias pantallas de estado que muestran el progreso de la instalación. Después de que el instalador termine la instalación, es el momento de seleccionar los conjuntos de características o las cargas de trabajo.

## <a name="install-workloads"></a>Instalar cargas de trabajo  
 Ahora, puede personalizar su instalación con cargas de trabajo. Seleccione una o varias cargas de trabajo; cada una contiene las características que necesita para el lenguaje de programación o la plataforma que prefiera.  

 A continuación se indica cómo obtenerlas.  

1.  Busque la carga de trabajo que quiera en la pantalla **Instalando Visual Studio**.  

  ![Cuadro de diálogo instalación de Visual Studio 2017 RC](../ide/media/willow1.png "Instalando Visual Studio 2017")

     Por ejemplo, elija la carga de trabajo de desarrollo de escritorio de .NET. Incluye el editor principal predeterminado, que contiene compatibilidad de edición de código básica para más de 20 lenguajes, la capacidad de abrir y editar código desde cualquier carpeta sin necesitar un proyecto y control de código fuente integrado.  

2.  Después de que seleccione las cargas de trabajo que quiera, haga clic en **Instalar**.  

    Después, aparecerán las pantallas de estado que muestran el progreso de su instalación de Visual Studio.

3.  Después de que se instalen los nuevos componentes y cargas de trabajo, haga clic en **Iniciar**.

## <a name="install-individual-components"></a>Instalar componentes individuales

Si no quiere usar la característica útil de cargas de trabajo para personalizar la instalación de Visual Studio, haga clic en la opción **Componentes individuales** desde el instalador de Visual Studio, seleccione lo que quiera y, después, siga las indicaciones.

  ![Visual Studio 2017 - Instalar componentes individuales](media/vs2017install-IndividualComponents.PNG "Instalar componentes individuales de Visual Studio")

## <a name="install-language-packs"></a>Instalar paquetes de idioma

Para instalar Visual Studio 2017 RC en un idioma de su elección, haga clic en la opción **Paquetes de idioma** desde el instalador de Visual Studio y siga las indicaciones.

  ![Visual Studio 2017 - Instalar paquetes de idioma](media/vs2017install-LanguagePacks.PNG "Instalar paquetes de idioma de Visual Studio")

### <a name="change-the-installer-language"></a>Cambiar el idioma del instalador

De manera predeterminada, el programa instalador intenta hacer coincidir el idioma del sistema operativo cuando se ejecuta por primera vez. El instalador recordará esta configuración. Puede cambiar esta configuración ejecutando el instalador desde la línea de comandos. Por ejemplo, puede ejecutar `vs_installer.exe --locale en-US` para forzar al instalador a utilizar el inglés. Esta configuración se recordará más tarde cuando el instalador se ejecute la próxima vez. El instalador admite los siguientes tokens de idioma: zh-CN, zh-TW, cs-CZ, en-US, fr-FR, de-DE, it-IT, ja-JP, ko-KR, pl-PL, pt-BR, ru-RU, es-ES y tr-TR.


  > [!IMPORTANT]
  > A pesar de que, en general, se admite el uso de Visual Studio 2017 RC en un entorno de producción, las cargas de trabajo y los componentes que aparecen marcados como "Versión preliminar" en la interfaz de usuario de instalación no son compatibles para usarlos en un entorno de producción.

## <a name="see-also"></a>Vea también  
* [Modify Visual Studio 2017 RC](modify-visual-studio.md) (Modificar Visual Studio 2017 RC)
* [Desinstalar Visual Studio 2017 RC](uninstall-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Cómo notificar un problema con Visual Studio 2017](../ide/how-to-report-a-problem-with-visual-studio-2017.md)



<!--HONumber=Feb17_HO4-->


