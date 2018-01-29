---
title: "Crear una instalación sin conexión de Visual Studio | Microsoft Docs"
description: "Descubra cómo instalar Visual Studio sin conexión."
ms.custom: 
ms.date: 01/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-acquisition
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- offline installation [Visual Studio]
- offline install [Visual Studio]
- layout [Visual Studio]
ms.assetid: f8625d5e-f6ea-4db0-83c0-619b77fab3cf
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: b9badba3247846ce63b79d48da7482ff0c58b693
ms.sourcegitcommit: bd16e764134c436d2d2f46490f51234d5246ee50
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="create-an-offline-installation-of-visual-studio-2017"></a>Crear una instalación sin conexión de Visual Studio 2017

Hemos diseñado un instalador de Visual Studio 2017 que funciona bien en una amplia variedad de condiciones de red y máquina.

- El nuevo modelo basado en la carga de trabajo implica que deberá descargar mucho menos contenido que con las versiones anteriores de Visual Studio: tan solo 300 MB para la instalación más pequeña.
- En comparación con un archivo ZIP o "ISO" genérico, solo se descargan los paquetes necesarios para su equipo. Por ejemplo, no se descargan los archivos de 64 bits si no los necesita.
- Durante el proceso de instalación, probaremos tres tecnologías de descarga diferentes (WebClient, BITS y WinInet) para minimizar la interferencia con software antivirus y de servidor proxy.
- Los archivos que necesitará para instalar Visual Studio se distribuyen en una red de entrega global, así que podemos obtenerlos de un servidor local.

Se recomienda probar el [instalador web de Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL), ya que creemos que será una buena experiencia.

 > [!div class="button"]
 > [Descargar Visual Studio 2017](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocsOL)
<br/>

Si quiere realizar una instalación sin conexión porque su conexión de Internet no está disponible o no es confiable, vea [Instalación de Visual Studio 2017 en entornos de red de bajo ancho de banda o poco confiables](../install/install-vs-inconsistent-quality-network.md). Puede usar la línea de comandos para crear una caché local de los archivos necesarios para completar una instalación sin conexión. Este proceso reemplaza los archivos ISO disponibles para las versiones anteriores.

> [!NOTE]
> Si es un administrador de empresa que quiere realizar una implementación de Visual Studio 2017 en una red de estaciones de trabajo del cliente con firewall desde Internet, vea las páginas [Creación de una instalación de red de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) y [Instalar los certificados necesarios para la instalación sin conexión de Visual Studio](../install/install-certificates-for-visual-studio-offline.md).

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, consulte la página [Troubleshooting Visual Studio 2017 installation and upgrade issues](troubleshooting-installation-issues.md) (Solucionar problemas de errores de instalación y actualización de Visual Studio 2017). Si ninguno de los pasos de solución de problemas ayuda, puede ponerse en contacto con nosotros por chat para obtener asistencia para la instalación (solo en inglés). Para más información, consulte la [página de soporte técnico de Visual Studio](https://www.visualstudio.com/vs/support/#talktous).

Aquí tiene algunas opciones de soporte técnico más:
* Puede notificarnos problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) que aparece en el instalador y en el IDE de Visual Studio.
* Puede compartir una sugerencia de producto con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579).
* Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), y hacer preguntas y encontrar respuestas.
* También puede ponerse en contacto con nosotros y otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio).  (Esta opción requiere una cuenta de [GitHub](https://github.com/)).
