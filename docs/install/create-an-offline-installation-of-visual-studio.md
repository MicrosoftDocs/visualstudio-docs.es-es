---
title: "Crear una instalación sin conexión de Visual Studio | Microsoft Docs"
description: "Descubra cómo instalar Visual Studio sin conexión."
ms.custom: 
ms.date: 08/30/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-install
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
ms.openlocfilehash: 8b0902c7e2d3c2b51ecd915647a3e8a03e49c641
ms.sourcegitcommit: 26419ab0cccdc30d279c32d6a841758cfa903806
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/11/2017
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
> Si es un administrador de empresa que quiere realizar una implementación de Visual Studio 2017 en una red de estaciones de trabajo del cliente con firewall desde Internet, vea las páginas [Creación de una instalación de red de Visual Studio 2017](../install/create-a-network-installation-of-visual-studio.md) y [Special considerations for installing Visual Studio in an offline environment](../install/install-visual-studio-in-offline-environment.md) (Consideraciones especiales para instalar Visual Studio en un entorno sin conexión).

## <a name="get-support"></a>Obtener soporte técnico
En ocasiones, algo no sale según lo previsto. Si se produce un error en la instalación de Visual Studio, vea sugerencias para la solución de problemas en la página [Solucionar problemas de errores de instalación y actualización de Visual Studio 2017](troubleshooting-installation-issues.md). Asimismo, puede informarnos de problemas del producto a través de la herramienta [Notificar un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) del IDE de Visual Studio o compartir una sugerencia con nosotros en [UserVoice](https://visualstudio.uservoice.com/forums/121579). Puede realizar el seguimiento de los problemas del producto en la [comunidad de desarrolladores de Visual Studio](https://developercommunity.visualstudio.com/), hacer preguntas y encontrar respuestas. También puede comunicarse con nosotros y con otros desarrolladores de Visual Studio a través de nuestra [conversación de Visual Studio en la Comunidad de Gitter](https://gitter.im/Microsoft/VisualStudio) (requiere una cuenta de [GitHub](https://github.com/)).
