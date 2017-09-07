---
title: "Instalación en entornos de red de bajo ancho de banda o poco confiables | Microsoft Docs"
description: "Se describe cómo funciona el instalador de Visual Studio en condiciones de red poco confiables y se explica cómo descargar archivos de instalación antes de comenzar la instalación."
ms.date: 08/25/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 44DB1998-68CD-4560-870A-EE5B993DCF6E
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 4a36302d80f4bc397128e3838c9abf858a0b5fe8
ms.openlocfilehash: 76ce76f7598cdff5a6f32fd871357af622ebfa72
ms.contentlocale: es-es
ms.lasthandoff: 09/06/2017

---

# <a name="install-visual-studio-2017-on-low-bandwidth-or-unreliable-network-environments"></a>Instalación de Visual Studio 2017 en entornos de red de bajo ancho de banda o poco confiables
Hemos diseñado un nuevo instalador de Visual Studio 2017 que funciona bien en una amplia variedad de condiciones de red y máquina.

- Los archivos que necesitará para instalar Visual Studio se distribuyen en una red de entrega global, así que podemos obtenerlos de un servidor local.
- Durante el proceso de instalación, probaremos tres tecnologías de descarga diferentes (WebClient, BITS y WinInet) para minimizar la interferencia con software antivirus y de servidor proxy.
- En comparación con un archivo ZIP o "ISO" genérico, solamente se descargan los paquetes que necesita para la máquina. No se descargan, por ejemplo, los archivos de 64 bits si no los necesita;
- El nuevo modelo basado en la carga de trabajo significa que necesitará descargar mucho menos que con las versiones anteriores de Visual Studio: tan poco como 300 MB para la instalación más pequeña.

Por lo tanto, se recomienda probar el nuevo instalador web, creemos que será una grata experiencia. Pero si desea asegurarse de que ha descargado correctamente los archivos de instalación antes de comenzar a instalar Visual Studio, tenemos lo que necesita. Puede usar la línea de comandos para crear una caché local de los archivos necesarios antes de iniciar la instalación.

Esta es la manera de hacerlo.

## <a name="download-the-visual-studio-bootstrapper"></a>Descarga del programa previo de Visual Studio
Para comenzar, descargue el programa previo de Visual Studio para la edición elegida de Visual Studio.

Su archivo de instalación&mdash;o, para ser más exactos, un archivo de programa previo&mdash;corresponderá o será parecido a uno de los siguientes:

| Edición                    | Archivo                                                                    |
|----------------------------|-------------------------------------------------------------------------|
| Comunidad de Visual Studio    | [vs_community.exe](https://aka.ms/vs/15/release/vs_community.exe)       |
| Visual Studio Professional | [vs_professional.exe](https://aka.ms/vs/15/release/vs_professional.exe) |
| Visual Studio Enterprise   | [vs_enterprise.exe](https://aka.ms/vs/15/release/vs_enterprise.exe)     |

## <a name="create-a-local-install-cache"></a>Creación de una caché de instalación local
Para crear un diseño local, abra un símbolo del sistema y use uno de los comandos de los ejemplos siguientes. En ellos se asume que está usando la edición Community de Visual Studio; ajuste el comando como sea adecuado para su edición.

- Para el desarrollo web y de escritorio .NET, ejecute:
```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

- Para el desarrollo de escritorio .NET y Office, ejecute:
```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.Office --includeOptional --lang en-US
```

- Para el desarrollo de escritorio C++, ejecute:
```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.NativeDesktop --includeRecommended --lang en-US
```

- Para crear un diseño local completo con todas las características (lo que llevará mucho tiempo ya que tenemos _multitud_ de características!), ejecute:
```
vs_community.exe --layout c:\vs2017layout --lang en-US
```

Si quiere instalar un idioma distinto del inglés, cambie `en-US` a una configuración regional de la lista en la parte inferior de esta página. Use esta [lista de los componentes y las cargas de trabajo disponibles](workload-and-component-ids.md) para personalizar aún más su caché de instalación según sea necesario.

## <a name="install-from-the-local-cache"></a>Instalación desde la caché local
> [!TIP]
> Cuando se trabaje desde una caché de instalación local, usaremos la versión local de cada uno de estos archivos. Sin embargo, si selecciona componentes durante la instalación que no se encuentran en la caché, intentaremos descargarlos de Internet.

Para asegurarse de que solo instala los archivos que ha descargado, use las mismas opciones de la línea de comandos que utilizó para crear la caché de diseño. Por ejemplo, si creó una caché de diseño con el siguiente comando:
```
vs_community.exe --layout c:\vs2017layout --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional --lang en-US
```

use este comando para ejecutar la instalación:
```
c:\vs2017layout\vs_community.exe --add Microsoft.VisualStudio.Workload.ManagedDesktop --add Microsoft.VisualStudio.Workload.NetWeb --add Component.GitHub.VisualStudio --includeOptional
```

## <a name="list-of-language-locales"></a>Lista de configuraciones regionales de idioma
| **Idioma-configuración regional** | **Idioma** |
| ----------------------- | --------------- |  
| cs-CZ | Checo |
| de-DE | Alemán |
| en-US | Inglés |
| es-ES | Español |
| fr-FR | Francés |
| it-IT | Italiano |
| ja-JP | Japonés |
| ko-KR | Coreano |
| pl-PL | Polaco |
| pt-BR | Portugués (Brasil) |
| ru-RU | Ruso |
| tr-TR | Turco |
| zh-CN | Chino (simplificado) |
| zh-TW | Chino (tradicional) |

## <a name="see-also"></a>Vea también
* [Instalar Visual Studio](install-visual-studio.md)
* [Guía del administrador de Visual Studio](visual-studio-administrator-guide.md)
* [Usar parámetros de la línea de comandos para instalar Visual Studio](use-command-line-parameters-to-install-visual-studio.md)

