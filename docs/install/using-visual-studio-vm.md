---
title: "Uso de Visual Studio en una máquina virtual de Azure | Microsoft Docs"
description: "Aprenda a usar Visual Studio en una máquina virtual de Azure"
ms.date: 01/30/2018
ms.technology: vs-acquisition
ms.topic: article
helpviewer_keywords:
- azure services
- virtual machine; VM
- installation
- visual studio
author: PhilLee-MSFT
ms.author: phillee
manager: sacalla
ms.workload:
- multiple
ms.openlocfilehash: d8e99965867d5dbc2710d6c56c5b3dc90fc16dc8
ms.sourcegitcommit: 4b4027244b8de25e30b533148804b87321d3e8a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 02/03/2018
---
# <a id="top"> </a> Imágenes de Visual Studio en Azure
El uso de Visual Studio en ejecución en una máquina virtual de Azure preconfigurada es la forma más fácil y rápida de llegar a un entorno de desarrollo en funcionamiento partiendo de cero.  Hay imágenes del sistema con distintas configuraciones de Visual Studio disponibles en [Azure Marketplace](https://portal.azure.com/). Basta con arrancar una máquina virtual y listo.

¿Es la primera vez que usa Azure? [Cree una cuenta gratuita de Azure](https://azure.microsoft.com/free).

## <a name="what-configurations-and-versions-are-available"></a>¿Qué configuraciones y versiones están disponibles?
En Azure Marketplace, encontrará imágenes de las versiones principales más recientes: Visual Studio 2017 y Visual Studio 2015.  En cada versión principal podrá ver la versión de lanzamiento original (también denominada versión "RTW") y las versiones actualizadas "más recientes".  Para cada una de las distintas versiones, busque Visual Studio Enterprise Edition y Visual Studio Community Edition.  Actualizamos estas imágenes como mínimo cada mes para incluir las actualizaciones más recientes de Visual Studio y Windows.  Aunque los nombres de las imágenes siguen siendo los mismos, la descripción de cada imagen incluye la versión del producto instalada y la fecha de inicio de la imagen.

|               Versión de lanzamiento              |        Ediciones       |     Versión del producto     |
|:------------------------------------------:|:---------------------:|:-----------------------:|
| Visual Studio 2017: versión más reciente (15.5) | Enterprise, Community |      Versión 15.5.3     |
|         Visual Studio 2017: RTW           | Enterprise, Community |      Versión 15.0.7     |
|   Visual Studio 2015: versión más reciente (Update 3)   | Enterprise, Community |  Versión 14.0.25431.01  |
|         Visual Studio 2015: RTW           |         Ninguna          | (Servicio de mantenimiento expirado) |

> [!NOTE]
> De conformidad con la directiva de mantenimiento de Microsoft, el servicio de mantenimiento de la versión de lanzamiento original (también denominada "RTW") de Visual Studio 2015 ha expirado.  Por lo tanto, Visual Studio 2015 Update 3 es la única versión que se ofrece con la línea de productos de Visual Studio 2015.

Para más información, consulte la [directiva de mantenimiento de Visual Studio](https://www.visualstudio.com/en-us/productinfo/vs-servicing-vs).

## <a name="what-features-are-installed"></a>¿Qué características están instaladas?
Cada imagen contiene el conjunto de características recomendado para esa edición de Visual Studio.  Por lo general, la instalación incluye:

* Todas las cargas de trabajo disponibles que incluyan los componentes opcionales recomendados para cada carga de trabajo
* SDK, paquetes de destino y herramientas de desarrollo de .NET 4.6.2 y .NET 4.7
* Visual F#
* Extensión de GitHub para Visual Studio
* Herramientas de LINQ to SQL

Esta es la línea de comandos que se usa para instalar Visual Studio al compilar las imágenes:

```
    vs_enterprise.exe --allWorkloads --includeRecommended --passive ^
       add Microsoft.Net.Component.4.7.SDK ^
       add Microsoft.Net.Component.4.7.TargetingPack ^ 
       add Microsoft.Net.Component.4.6.2.SDK ^
       add Microsoft.Net.Component.4.6.2.TargetingPack ^
       add Microsoft.Net.ComponentGroup.4.7.DeveloperTools ^
       add Microsoft.VisualStudio.Component.FSharp ^
       add Component.GitHub.VisualStudio ^
       add Microsoft.VisualStudio.Component.LinqToSql
```

Si las imágenes no incluyen la característica de Visual Studio que necesita, envíe un comentario mediante la herramienta para crear comentarios que se encuentra en la esquina superior derecha de la página.

## <a name="what-size-vm-should-i-choose"></a>¿Qué tamaño de máquina virtual debería elegir?
El aprovisionamiento de una nueva máquina virtual es muy sencillo y Azure ofrece toda la gama de tamaños de máquina virtual.  Igual que sucede cuando compra cualquier tipo de hardware, lo que le interesa es conseguir una buena relación entre el rendimiento y el costo.  Dado que Visual Studio es una eficaz aplicación multiproceso, es recomendable que la máquina tenga un tamaño que pueda incluir al menos dos procesadores y 7 GB de memoria. En Azure eso se traduce en al menos los siguientes tamaños de máquina virtual:

   * Standard_D2_v3
   * Standard_D2s_v3
   * Standard_D4_v3
   * Standard_D4s_v3
   * Standard_D2_v2
   * Standard_D2S_v2
   * Standard_D3_v2

Para más información sobre los tamaños de máquina más recientes, consulte [Tamaños de las máquinas virtuales Windows en Azure](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/sizes).

Con Azure no se verá limitado a su primera elección: puede reequilibrar su opción inicial cambiando el tamaño de la máquina virtual.  También puede aprovisionar una nueva máquina virtual con un tamaño más adecuado o cambiar el tamaño de la máquina virtual existente en otro hardware subyacente.  Para más información, consulte [Cambio de tamaño de una máquina virtual Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/resize-vm).

## <a name="after-i-get-the-vm-running-then-what"></a>Ya he puesto en marcha la máquina virtual, ¿ahora qué?
Visual Studio sigue el modelo "traiga su propia licencia" de Azure.  Así pues, igual que sucede en la instalación de hardware propietario, uno de los primeros pasos es obtener una licencia para la instalación de Visual Studio.  Para desbloquear Visual Studio, puede iniciar sesión con una cuenta de Microsoft que esté asociada a una suscripción a Visual Studio o usar la clave de producto que se proporciona con la compra inicial.  Para más información, consulte [Iniciar sesión en Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/signing-in-to-visual-studio) y [Cómo desbloquear Visual Studio](https://docs.microsoft.com/en-us/visualstudio/ide/how-to-unlock-visual-studio).

## <a name="after-i-build-out-the-dev-vm-how-do-i-save-capture-it-for-future-or-team-use"></a>Después de compilar la máquina virtual de desarrollo, ¿cómo puedo guardarla o capturarla para usarla más adelante o para que la utilice mi equipo?

Hay una amplia gama de entornos de desarrollo y, si quiere compilar uno de los entornos más complejos, esto le supondrá un costo significativo.  Pero, con independencia de la configuración del entorno, Azure le permite conservar su inversión fácilmente; para ello, se guarda o captura la máquina virtual que ya esté configurada como "imagen base" para que usted o su equipo puedan usarla en un futuro.  Después, al arrancar la nueva máquina virtual, se aprovisionará a partir de la imagen base y no de la imagen de Marketplace.

A modo de rápido resumen, tendrá que ejecutar Sysprep y apagar la máquina virtual en ejecución y, luego, *capturar (figura 1)* la máquina virtual como imagen mediante la interfaz de usuario de Azure Portal.  Azure guarda el archivo `.vhd` que contiene la imagen en la cuenta de almacenamiento que se elija.  Después, la nueva imagen aparecerá como recurso de imagen en la lista de recursos de la suscripción.

<img src="media/capture-vm.png" alt="Capture an image through the Azure portal’s UI" style="border:3px solid Silver; display: block; margin: auto;"><center>*(Figura 1) Captura de una imagen mediante la interfaz de usuario de Azure Portal.*</center>

Para más información, consulte [Captura de una máquina virtual en una imagen](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/capture-image-resource).

  **Aviso:** No olvide ejecutar Sysprep en la máquina virtual.  Si se salta este paso, Azure no podrá aprovisionar una máquina virtual a partir de la imagen.

> [!NOTE]
> Se sigue generando algún costo por el almacenamiento de las imágenes, pero es probable que ese costo incremental sea insignificante en comparación con los costos en recursos humanos para recompilar la máquina virtual desde el principio para cada persona del equipo que necesita una máquina virtual.  Por ejemplo, crear y almacenar una imagen de 127 GB durante un mes que todos los miembros del equipo pueden reutilizar cuesta unos cuantos dólares.  Pero, estos costos son insignificantes en comparación con las horas que invierte cada empleado en compilar y validar un paquete de desarrollo configurado correctamente para su uso individual.

Además, puede que las tecnologías o las tareas de desarrollo requieran mayor escalado (como variedades de configuraciones de desarrollo y varias configuraciones de máquina).  Puede usar Azure DevTest Labs para crear _recetas_ que automatizan la construcción de la "imagen perfecta" y administrar directivas para las máquinas virtuales en ejecución del equipo.  [Uso de Azure DevTest Labs para desarrolladores](https://docs.microsoft.com/en-us/azure/devtest-lab/devtest-lab-developer-lab) es la mejor fuente de información sobre DevTest Labs.

## <a name="next-steps"></a>Pasos siguientes
Ahora que ya está informado sobre las imágenes preconfiguradas de Visual Studio, el siguiente paso es crear una máquina virtual:

* [Creación de una máquina virtual en Azure Portal](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/quick-create-portal)
* [Información general sobre las máquinas virtuales Windows](https://docs.microsoft.com/en-us/azure/virtual-machines/windows/overview)
