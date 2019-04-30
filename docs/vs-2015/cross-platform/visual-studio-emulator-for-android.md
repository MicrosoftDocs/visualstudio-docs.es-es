---
title: Emulador de Visual Studio para Android | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: tgt-pltfrm-cross-plat
ms.topic: conceptual
ms.assetid: 80f0104f-a4db-44dd-bd55-37bb67776c62
caps.latest.revision: 7
ms.author: crdun
manager: crdun
ms.openlocfilehash: a33d7928e6e2555f0cfd484059b062ae801d8633
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "63442090"
---
# <a name="visual-studio-emulator-for-android"></a>Emulador de Visual Studio para Android
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

El Emulador de Visual Studio para Android es una aplicación de escritorio que emula un dispositivo Android. Proporciona un entorno virtualizado en el que puede depurar y probar aplicaciones Android sin un dispositivo físico. También ofrece un entorno aislado para sus prototipos de aplicación.  
  
 El Emulador de Visual Studio para Android está diseñado para proporcionar un rendimiento comparable al de un dispositivo real. Sin embargo, antes de publicar la aplicación le recomendamos que la pruebe en un dispositivo físico.  
  
 Puede probar la aplicación en un perfil de dispositivo único para cada una de las plataformas Android, resoluciones de pantalla y otras propiedades de hardware compatibles con el Emulador de Visual Studio para Android.  
  
 Este tema contiene las siguientes secciones:  
  
- [Instalación y desinstalación](#Installing)  
  
- [Requisitos del sistema y compatibilidad con versiones anteriores](#Requirements)  
  
- [Funciones de red en el Emulador de Visual Studio para Android](#Networking)  
  
- [Configuración del Emulador de Visual Studio para Android](#Configuring)  
  
- [Características que puede probar en el emulador](#FeaturesTest)  
  
- [Características que no puede probar en el emulador](#FeaturesNonTest)  
  
- [Recursos de soporte técnico](#Support)  
  
## <a name="Installing"></a> Instalación y desinstalación  
 Instalación  
  
 El Emulador de Visual Studio para Android es un componente de las herramientas de desarrollo multiplataforma disponibles en Visual Studio, y se instalará durante una instalación personalizada de Visual Studio si selecciona Desarrollo para móviles entre plataformas, Kits de desarrollo de software y herramientas comunes y, por último, Emulador de Visual Studio para Android.  
  
 Desinstalación  
  
 Puede desinstalar el emulador de Visual Studio para Android mediante la opción Agregar o quitar programas del Panel de control.  
  
> [!NOTE]
> Al desinstalar Visual Studio no se desinstalará el emulador; debe desinstalar el emulador por separado.  
  
 Cuando desinstala el Emulador de Visual Studio para Android, los adaptadores Ethernet virtuales Hyper-V que se crearon para su uso no se quitan automáticamente. Puede quitar manualmente estos adaptadores virtuales (si no están en uso); para ello, abra el Administrador de Hyper-V, seleccione una de las imágenes de disco duro virtual del emulador, seleccione la pestaña Funciones de red y seleccione **Quitar** para todos los modificadores que aparecen en esta pestaña.  
  
## <a name="Requirements"></a> Requisitos del sistema y compatibilidad con versiones anteriores  
 Para obtener información importante sobre los requisitos de hardware, software y configuración del emulador de Visual Studio para Android, vea el siguiente tema.  
  
- [System Requirements for the Visual Studio Emulator for Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)  
  
  El Emulador de Visual Studio para Android requiere Visual Studio de 2015; no es compatible con versiones anteriores de Visual Studio.  
  
  Las nuevas versiones del emulador se instalan sobre las versiones anteriores (y pueden, en algunos casos, reemplazar las imágenes anteriores y descartar la configuración, las aplicaciones y los archivos instalados en dichas imágenes).  
  
## <a name="Networking"></a> Funciones de red en el Emulador de Visual Studio para Android  
 La conexión de red del Emulador de Visual Studio para Android se comporta como la conexión de un equipo de escritorio, con estas características:  
  
- El emulador aparece en la red como un dispositivo independiente, con su propia dirección IP.  
  
- No se requiere ningún software de red adicional que no se instale ya con el emulador.  
  
- No se une a un dominio de Windows.  
  
  Para comprender las capacidades de la conexión de red del emulador, piense que es similar a la conexión Wi-Fi de un teléfono Android a la misma red. Si una aplicación que se ejecuta en el teléfono puede acceder a un recurso de red a través de su conexión Wi-Fi, una aplicación que se ejecuta en el emulador puede acceder el mismo recurso de red.  
  
  Para obtener más información sobre los requisitos de red, vea [Requisitos del sistema del Emulador de Visual Studio para Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md).  
  
  Para obtener información sobre cómo solucionar problemas de red, vea [Solución de problemas del Emulador de Visual Studio para Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md).  
  
## <a name="Configuring"></a> Configuración del Emulador de Visual Studio para Android  
 Probar la compatibilidad de una aplicación Android con la enorme variedad de hardware Android puede suponer un desafío. Los teléfonos y tabletas Android en el mercado abarcan una amplia gama de versiones y tamaños de pantalla, con muchas configuraciones de hardware distintas (RAM, CPU, arquitectura, etc.). El Emulador de Visual Studio para Android simplifica todo esto mediante los perfiles de dispositivo. Nuestro conjunto de perfiles de dispositivo representa el hardware más popular del mercado, incluidos los dispositivos de Samsung, Motorola, Sony, LG y otros muchos.  
  
 En Visual Studio 2015 puede instalar, desinstalar e iniciar perfiles de dispositivo mediante el Administrador del emulador. Puede acceder al Administrador del emulador eligiendo **Herramientas** y **Emulador de Visual Studio para Android**.  
  
 ![Administrador del Emulador de Visual Studio para Android](../cross-platform/media/android-emu-manager.png "Android_Emu_Manager")  
  
 De forma predeterminada, existen cuatro perfiles de dispositivo preinstalados (configuraciones KitKat y de círculo para teléfonos de 5 pulgadas y tabletas de 7 pulgadas), como se indica en el texto en blanco y los iconos. Los demás perfiles de la lista aparecerán en gris hasta que use el botón **Instalar perfil** y complete su instalación. Puede filtrar la lista por nivel de API y hacer clic en la flecha de detalles, en el lado inferior derecho de un perfil, para ver sus detalles completos de configuración.  
  
 Una vez haya instalado el conjunto de perfiles que quiere, puede iniciarlos directamente desde el Administrador pulsando el botón verde **Reproducir**. También aparecerá en el menú desplegable Destino de depuración en cualquier tipo de proyecto móvil multiplataforma de Visual Studio.  
  
## <a name="FeaturesTest"></a> Características que puede probar en el emulador  
 Para obtener información detallada sobre las características que puede probar en el emulador, vea esta [documentación](http://blogs.msdn.com/b/visualstudioalm/archive/2014/11/12/introducing-visual-studio-s-emulator-for-android.aspx).  
  
## <a name="FeaturesNonTest"></a> Características que no puede probar en el emulador  
 La lista siguiente describe características de la plataforma Android que **no puede** probar en el emulador. Deberá probarlas en un dispositivo físico.  
  
- Brújula  
  
- Giroscopio  
  
- Controlador de vibración  
  
- Luminosidad. Cambiar el nivel de luminosidad del emulador no afecta al modo en que el dispositivo aparece en la pantalla.  
  
## <a name="Support"></a> Recursos de soporte técnico  
 Si el equipo host cumple los requisitos del sistema y detecta un problema que no se trata en esta guía de solución de problemas:  
  
- Formule una pregunta en StackOverflow con las etiquetas [android-emulator](http://stackoverflow.com/questions/tagged/android-emulator) y visual-studio.  
  
- Notifique un problema con la herramienta Enviar una sonrisa en Visual Studio o en el administrador del emulador.  
  
## <a name="see-also"></a>Vea también  
 [Requisitos de sistema del emulador de Visual Studio para Android](../cross-platform/system-requirements-for-the-visual-studio-emulator-for-android.md)   
 [Troubleshooting the Visual Studio Emulator for Android](../cross-platform/troubleshooting-the-visual-studio-emulator-for-android.md)
